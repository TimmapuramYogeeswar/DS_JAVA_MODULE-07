# Flattening a Nested List Using an Iterator
## DATE:16-11-2025
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1.Start the program.

2.Define an interface-like class NestedInteger that can represent either a single integer or a nested list.

3.Use a stack or recursion to flatten all integers from the nested list into a single list.

4.Store the flattened list and maintain an index to track the current element.

5.Implement next() to return the next integer and hasNext() to check if more integers exist.

6.Test the iterator with a sample nested list.

7.Stop the program.  

## Program:
```
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: TIMMAPURAM YOGEESWAR
RegisterNumber: 212223230233
import java.util.*;
interface NestedInteger {
    boolean isInteger();
    Integer getInteger();
    List<NestedInteger> getList();
}

class NestedIntegerImpl implements NestedInteger {
    private Integer value;
    private List<NestedInteger> list;

    public NestedIntegerImpl(int value) {
        this.value = value;
        this.list = null;
    }

    public NestedIntegerImpl(List<NestedInteger> list) {
        this.list = list;
        this.value = null;
    }

    @Override
    public boolean isInteger() {
        return value != null;
    }

    @Override
    public Integer getInteger() {
        return value;
    }

    @Override
    public List<NestedInteger> getList() {
        return list;
    }
}

class NestedIterator implements Iterator<Integer> {

    private Stack<NestedInteger> stack = new Stack<>();

    public NestedIterator(List<NestedInteger> nestedList) {
        for (int i = nestedList.size() - 1; i >= 0; i--) {
            stack.push(nestedList.get(i));
        }
    }

    @Override
    public Integer next() {
        return stack.pop().getInteger();
    }

    @Override
    public boolean hasNext() {
        while (!stack.isEmpty()) {
            NestedInteger top = stack.peek();

            if (top.isInteger()) return true;

            stack.pop();

            List<NestedInteger> list = top.getList();
            for (int i = list.size() - 1; i >= 0; i--) {
                stack.push(list.get(i));
            }
        }
        return false;
    }
}

public class Main {
    public static void main(String[] args) {

        List<NestedInteger> nestedList = new ArrayList<>();

        nestedList.add(new NestedIntegerImpl(1));

        List<NestedInteger> innerList2 = new ArrayList<>();
        innerList2.add(new NestedIntegerImpl(4));

        List<NestedInteger> innerList3 = new ArrayList<>();
        innerList3.add(new NestedIntegerImpl(6));

        innerList2.add(new NestedIntegerImpl(innerList3));

        nestedList.add(new NestedIntegerImpl(innerList2));
        nestedList.add(new NestedIntegerImpl(2));

        NestedIterator it = new NestedIterator(nestedList);

        System.out.print("Flattened list: ");
        while (it.hasNext()) {
            System.out.print(it.next() + " ");
        }
    }
}

*/
```

## Output:
<img width="373" height="69" alt="image" src="https://github.com/user-attachments/assets/94e23941-2b03-4919-94cb-67732cb572c3" />



## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
