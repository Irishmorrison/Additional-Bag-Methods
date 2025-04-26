# Additional-Bag-Methods

Here is the Bag.Java Code:

import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

/**
 * A generic Bag class implementing the bag data structure with additional methods.
 * @param <T> the type of elements stored in the bag
 */
public class Bag<T> {
    private List<T> items; // List to store bag elements

    /**
     * Constructor to initialize the bag.
     */
    public Bag() {
        this.items = new ArrayList<>();
    }

    /**
     * Adds an item to the bag.
     * @param item the item to add
     */
    public void add(T item) {
        items.add(item);
    }

    /**
     * Removes one occurrence of the specified item from the bag, if it exists.
     * @param item the item to remove
     */
    public void remove(T item) {
        items.remove(item); // removes first occurrence if exists
    }

    /**
     * Checks if the bag contains the specified item.
     * @param item the item to check
     * @return true if item exists, false otherwise
     */
    public boolean contains(T item) {
        return items.contains(item);
    }

    /**
     * Counts the number of occurrences of the specified item in the bag.
     * @param item the item to count
     * @return the count of the item
     */
    public int count(T item) {
        int count = 0;
        for (T element : items) {
            if (element.equals(item)) {
                count++;
            }
        }
        return count;
    }

    /**
     * Returns the total number of elements in the bag, including duplicates.
     * @return size of the bag
     */
    public int size() {
        return items.size();
    }

    /**
     * Merges another bag into this bag by adding all its elements.
     * @param otherBag the bag to merge into this one
     */
    public void merge(Bag<T> otherBag) {
        this.items.addAll(otherBag.items);
    }

    /**
     * Creates and returns a new Bag containing only the distinct elements from this bag.
     * @return a new Bag with unique elements
     */
    public Bag<T> distinct() {
        Bag<T> distinctBag = new Bag<>();
        Set<T> seen = new HashSet<>();
        for (T item : items) {
            if (!seen.contains(item)) {
                seen.add(item);
                distinctBag.add(item);
            }
        }
        return distinctBag;
    }

    /**
     * Returns a string representation of the bag's contents.
     * @return string of all items
     */
    @Override
    public String toString() {
        return items.toString();
    }

    /**
     * Main method to demonstrate the additional methods.
     */
    public static void main(String[] args) {
        // Create two Bag instances
        Bag<String> bag1 = new Bag<>();
        Bag<String> bag2 = new Bag<>();

        // Add elements to bag1
        bag1.add("apple");
        bag1.add("banana");
        bag1.add("apple");
        bag1.add("orange");

        // Add elements to bag2
        bag2.add("banana");
        bag2.add("kiwi");
        bag2.add("banana");
        bag2.add("grape");

        // Print sizes
        System.out.println("Size of bag1: " + bag1.size()); // 4
        System.out.println("Size of bag2: " + bag2.size()); // 4

        // Merge bag2 into bag1
        bag1.merge(bag2);
        System.out.println("Contents of merged bag: " + bag1);

        // Create a bag with only distinct elements
        Bag<String> distinctBag = bag1.distinct();
        System.out.println("Distinct elements in merged bag: " + distinctBag);
    }
}
