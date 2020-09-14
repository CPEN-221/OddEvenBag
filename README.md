OddEvenBag: A Datatype Exercise
=========

> The skeleton source code for this question is in the package `oddevenbag`. You have to implement the required method in the class `OddEvenBag`. You may import the provided code as a Gradle project in Eclipse.

An `OddEvenBag` allows us to store `int`s (including duplicates) and perform some useful operations on the collection of `int`s.

Here are the essential operations that an `OddEvenBag` supports:

1. **Creators**
	1. Create an empty `OddEvenBag`
	2. Create an `OddEvenBag` using an array of `int`s as initial values
2. **Mutators**
	1. Add a given `int`
	2. Remove one occurrence of a given `int`
	3. Increment: increase the value of each entry by 1
	4. Decrement: decrease the value of each entry by 1
3. **Observers**
	1. Check if an `int` is in the `OddEvenBag`
	2. Return a count of the number of occurrences of an `int` in the bag
	3. Return the sum of the elements in the bag
	4. Verify equality: two `OddEvenBags` are equal if and only if they contain an identical quantity of odd numbers and an identical quantity of even numbers (the specific values do not matter here)
	5. A suitable hash code operation

### Specifications

```
// Create an empty OddEvenBag
OddEvenBag()

// Create an OddEvenBag using the elements in the provided array
// requires: seedArray is not null
OddEvenBag(int[] seedArray)

// add x to the OddEvenBag
add(int x)

// remove x from the OddEvenBag
// if x does not exist in the Bag then do nothing
void remove(int x)

// increment each value in the OddEvenBag by 1
void increment()

// decrement each value in the OddEvenBag by 1
void decrement()

// return true if this OddEvenBag contains x
// and false otherwise
boolean contains(int x)

// count the occurrences of x in the OddEvenBag
int getCount(int x)

// return the sum of the values in the OddEvenBag
long sum()
```

Although not listed above, `equals()` and `hashCode()` should be implemented.

### Test Cases

```java
@Test
public void test1() {
	OddEvenBag oeb = new OddEvenBag();
	oeb.add(10);
	assertTrue(oeb.contains(10));
	assertEquals(10, oeb.sum());
}

@Test
public void test2() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	assertTrue(oeb.contains(5));
	assertEquals(21, oeb.sum());
}

@Test
public void test3() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	oeb.increment();
	assertEquals(27, oeb.sum());
}

@Test
public void test4() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	oeb.decrement();
	assertEquals(15, oeb.sum());
}

@Test
public void test5() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 12, 14, 18, 3, 9, 11 });
	assertTrue(oeb1.equals(oeb2));
	assertTrue(oeb2.equals(oeb1));
	assertTrue(oeb1.hashCode() == oeb2.hashCode());
}

@Test
public void test7() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 1, 3, 6, 2, 4, 6 });
	assertTrue(!oeb1.equals(oeb2));
	assertTrue(!oeb2.equals(oeb1));
}

@Test
public void test8() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6, 8 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 1, 3, 7, 2, 4, 6, 10 });
	oeb1.increment();
	assertTrue(!oeb1.equals(oeb2));
	assertTrue(!oeb2.equals(oeb1));
}

@Test
public void test9() {
	OddEvenBag oeb = new OddEvenBag();
	String s = "abc";
	assertTrue(!oeb.equals(s));
}
```
