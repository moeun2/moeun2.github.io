---
title: DataStructure
tags: [CS, DataStructure]
style: fill
color: warning
description: DataStructure Summarizing
---



# 연결리스트(Linked List)

source : [GeeksforGeeks](https://www.geeksforgeeks.org/how-to-implement-generic-linkedlist-in-java/) , [gyoogle](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Linked%20List.md), [Programming Interviews Exposed 4th Edition](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=195800711)



![linkedlist](https://media.geeksforgeeks.org/wp-content/uploads/20210409184741/HowtoImplementGenericLinkedListinJava.jpg)

## 연결리스트란?

> 연속적인 메모리 윈치에 저장되지 않는 **선형 데이터 구조**
>
> 각 노드는 **데이터 필드**(value of the node) 와 **다음 노드에 대한 참조**(link to the next node를 포함하는 노드로 구성

<br>

## 왜 Linked List를 사용하나?

> **배열**은 비슷한 유형의 선형 데이터를 저장하는데 사용할 수 있지만 **제한 사항이 있음**
>
> 1. 배열의 **크기가 고정**되어 있어 **미리 요소의 수에 대해 할당**을 받아야 함
> 2. 새로운 요소를 **삽입**하는 것은 **비용이 많이 듬** (공간을 만들고, 기존 요소 전부 이동)

<br>

## 장점

> 동적 크기 / 삽입,삭제 용이

## 단점

> 임의로 엑세스 허용 X(첫번째 노드부터 순차적으로 엑세스 필요이,진 검색 수행  X) / 포인터를 위한 여분의 메모리 공간이 목록의 각 요소에 필요



## Member Function

 

- add (data): It adds an element at the end of the linked list
- add (position, data): It adds an element to any valid position in the linked list
- remove(key): It removes node that contains key from the linked list
- clear() : it clears the entire linked list
- empty(): It checks if the linked list is empty or not
- length(): It returns the length of the linked list

## Implementation

```java
// Java Program to Implement Generic Linked List

// Importing all input output classes
import java.io.*;

// Class 1
// Helper Class (Generic node class for LinkedList)
class node<T> {

	// Data members
	// 1. Storing value of node
	T data;
	// 2. Storing address of next node
	node<T> next;

	// Parameterized constructor to assign value
	node(T data)
	{
		// This keyword refers to current object itself
		this.data = data;
		this.next = null;
	}
}

// Class 2
// Helper class ( Generic LinkedList class)
class list<T> {

	// Generic node instance
	node<T> head;
	// Data member to store length of list
	private int length = 0;

	// Default constructor
	list() { this.head = null; }
	// Method
	// To add node at the end of List
	void add(T data)
	{

		// Creating new node with given value
		node<T> temp = new node<>(data);

		// Checking if list is empty
		// and assigning new value to head node
		if (this.head == null) {
			head = temp;
		}

		// If list already exists
		else {

			// Temporary node for traversal
			node<T> X = head;

			// Iterating till end of the List
			while (X.next != null) {
				X = X.next;
			}

			// Adding new valued node at the end of the list
			X.next = temp;
		}

		// Increasing length after adding new node
		length++;
	}

	// Method
	// To add new node at any given position
	void add(int position, T data)
	{

		// Checking if position is valid
		if (position > length + 1) {

			// Display message only
			System.out.println(
				"Position Unavailable in LinkedList");
			return;
		}

		// If new position is head then replace head node
		if (position == 1) {

			// Temporary node that stores previous head
			// value
			node<T> temp = head;

			// New valued node stored in head
			head = new node<T>(data);

			// New head node pointing to old head node
			head.next = temp;

			return;
		}

		// Temporary node for traversal
		node<T> temp = head;

		// Dummy node with null value that stores previous
		// node
		node<T> prev = new node<T>(null);
		// iterating to the given position
		while (position - 1 > 0) {
			// assigning previous node
			prev = temp;
			// incrementing next node
			temp = temp.next;
			// decreasing position counter
			position--;
		}
		// previous node now points to new value
		prev.next = new node<T>(data);
		// new value now points to former current node
		prev.next.next = temp;
	}
	// Method
	// To remove a node from list
	void remove(T key)
	{

		// NOTE
		// dummy node is used to represent the node before
		// the current node Since in a Singly Linked-List we
		// cannot go backwards from a node, we use a dummy
		// node to represent the previous node. In case of
		// head node, since there is no previous node, the
		// previous node is assigned to null.

		// Dummy node with null value
		node<T> prev = new node<>(null);

		// Dummy node pointing to head node
		prev.next = head;

		// Next node that points ahead of current node
		node<T> next = head.next;

		// Temporary node for traversal
		node<T> temp = head;

		// Boolean value that checks whether value to be
		// deleted exists or not
		boolean exists = false;

		// If head node needs to be deleted
		if (head.data == key) {
			head = head.next;

			// Node to be deleted exists
			exists = true;
		}

		// Iterating over LinkedList
		while (temp.next != null) {

			// We convert value to be compared into Strings
			// and then compare using
			// String1.equals(String2) method

			// Comparing value of key and current node
			if (String.valueOf(temp.data).equals(
					String.valueOf(key))) {

				// If node to be deleted is found previous
				// node now points to next node skipping the
				// current node
				prev.next = next;
				// node to be deleted exists
				exists = true;

				// As soon as we find the node to be deleted
				// we exit the loop
				break;
			}

			// Previous node now points to current node
			prev = temp;

			// Current node now points to next node
			temp = temp.next;

			// Next node points the node ahead of current
			// node
			next = temp.next;
		}

		// Comparing the last node with the given key value
		if (exists == false
			&& String.valueOf(temp.data).equals(
				String.valueOf(key))) {

			// If found , last node is skipped over
			prev.next = null;

			// Node to be deleted exists
			exists = true;
		}

		// If node to be deleted exists
		if (exists) {

			// Length of LinkedList reduced
			length--;
		}

		// If node to be deleted does not exist
		else {

			// Print statement
			System.out.println(
				"Given Value is not present in linked list");
		}
	}

	// Method
	// To clear the entire LinkedList
	void clear()
	{

		// Head now points to null
		head = null;
		// length is 0 again
		length = 0;
	}

	// Method
	// Returns whether List is empty or not
	boolean empty()
	{

		// Checking if head node points to null
		if (head == null) {
			return true;
		}
		return false;
	}
	// Method
	// Returning the length of LinkedList
	int length() { return this.length; }

	// Method
	// To display the LinkedList
	// @Override
	public String toString()
	{

		String S = "{ ";

		node<T> X = head;

		if (X == null)
			return S + " }";

		while (X.next != null) {
			S += String.valueOf(X.data) + " -> ";
			X = X.next;
		}

		S += String.valueOf(X.data);
		return S + " }";
	}
}

// Class 3
// Main Class
public class GFG {

	// main driver method
	public static void main(String[] args)
	{

		// Integer List

		// Creating new empty Integer linked list
		list<Integer> list1 = new list<>();
		System.out.println(
			"Integer LinkedList created as list1 :");
		// Adding elements to the above List object

		// Element 1 - 100
		list1.add(100);
		// Element 2 - 200
		list1.add(200);
		// Element 3 - 300
		list1.add(300);

		// Display message only
		System.out.println(
			"list1 after adding 100,200 and 300 :");

		// Print and display the above List elements
		System.out.println(list1);

		// Removing 200 from list1
		list1.remove(200);

		// Display message only
		System.out.println("list1 after removing 200 :");

		// Print and display again updated List elements
		System.out.println(list1);

		// String LinkedList

		// Creating new empty String linked list
		list<String> list2 = new list<>();
		System.out.println(
			"\nString LinkedList created as list2");
		// Adding elements to the above List object

		// Element 1 - hello
		list2.add("hello");

		// Element 2 - world
		list2.add("world");

		// Display message only
		System.out.println(
			"list2 after adding hello and world :");

		// Print current elements only
		System.out.println(list2);

		// Now, adding element 3- "GFG" at position 2
		list2.add(2, "GFG");

		// Display message only
		System.out.println(
			"list2 after adding GFG at position 2 :");

		// now print the updated List again
		// after inserting element at second position
		System.out.println(list2);

		// Float LinkedList

		// Creating new empty Float linked list
		list<Float> list3 = new list<>();

		// Display message only
		System.out.println(
			"\nFloat LinkedList created as list3");

		// Adding elements to the above List

		// Element 1 - 20.25
		list3.add(20.25f);
		// Element 2 - 50.42
		list3.add(50.42f);
		// Element 3 - 30.99
		list3.add(30.99f);

		// Display message only
		System.out.println(
			"list3 after adding 20.25, 50.42 and 30.99 :");

		// Print and display List elements
		System.out.println(list3);

		// Display message only
		System.out.println("Clearing list3 :");

		// Now.clearing this list using clear() method
		list3.clear();

		// Now, print and display the above list again
		System.out.println(list3);
	}
}

```

## Question 1

> 스택 자료구조에 대해 논하라. 연결리스트, 또는 동적 배열을 써서 C로 스택을 구현하고, 그 자료 구조를 사용한 이유를 설명하라. 완전하고 일관성 있으면서 사용하기 편리한 스택 인터페이스를 설계하라

