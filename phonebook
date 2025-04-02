import java.io.*;
import java.util.*;

public class PhonebookEntry {

    private Name name;
    private PhoneNumber phoneNumber;

    // Constructor to initialize PhonebookEntry with Name and PhoneNumber
    public PhonebookEntry(Name name, PhoneNumber phoneNumber) {
        this.name = name;
        this.phoneNumber = phoneNumber;
    }

    // Method to read input from Scanner and create a new PhonebookEntry
    public static PhonebookEntry read(Scanner sc) {
        if (!sc.hasNext()) return null; // Check if there is input to read
        String last = sc.next(); // Read last name
        String first = sc.next(); // Read first name
        String number = sc.next(); // Read phone number

        Name tname = new Name(last, first); // Create a Name object
        PhoneNumber phonenumber = new PhoneNumber(number); // Create a PhoneNumber object

        return new PhonebookEntry(tname, phonenumber); // Return new PhonebookEntry
    }

    // Getter for Name
    public Name getName() {
        return name;
    }

    // Getter for PhoneNumber
    public PhoneNumber getPhoneNumber() {
        return phoneNumber;
    }

    // Override toString method to display PhonebookEntry details
    public String toString() {
        return name + ": " + phoneNumber;
    }

    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner(new File("phonebook.text")); // Open file for reading

        int count = 0; // Counter for total phonebook entries
        ArrayList<PhonebookEntry> seensofar = new ArrayList<PhonebookEntry>(); // Stores all entries seen so far
        PhonebookEntry entry = read(scanner); // Read first entry
        ArrayList<Name> people = new ArrayList<Name>(); // Stores all names seen so far
        ArrayList<Integer> phonebookline = new ArrayList<Integer>(); // Stores line numbers of duplicate entries
        ArrayList<Integer> nameline = new ArrayList<Integer>(); // Stores line numbers of duplicate names
        PhonebookEntry duplicateEntry = null; // Keep track of previous PhonebookEntry object to check duplicate
        Name duplicateName = null;

        while (entry != null) {
            System.out.println(entry.toString()); // Print current entry
            count++; // Increment count of processed entries
            
            if (seensofar.contains(entry)) { // Check for duplicate phonebook entry
                duplicateEntry = entry;
            } else if (people.contains(entry.getName())) { // Check for duplicate name
                duplicateName = entry.getName();
            }
            
            seensofar.add(entry); // Store current entry
            people.add(entry.getName()); // Store current name
            entry = read(scanner); // Read next entry
        }
        
        System.out.println(count + " phonebook entries processed.");
        if (duplicateEntry != null || duplicateName != null) {
            System.out.println("Duplicates in file:");
            for (int i = 0; i < seensofar.size(); i++) {
                if (seensofar.get(i).equals(duplicateEntry)) {
                    phonebookline.add(i); // Store line number of duplicate entry
                } else if (seensofar.get(i).getName().equals(duplicateName)) {
                    nameline.add(i); // Store line number of duplicate name
                }
            }

            if (duplicateEntry != null) {
                System.out.println("Duplicate entries for " + duplicateEntry.toString() + "at lines " + phonebookline.get(0) + " and " + phonebookline.get(1));
            }
            else if (duplicateName != null){
                String newString = duplicateName.toString();
                String nameWord = newString.substring(0, newString.length() - 1);
                System.out.println("Duplicate names for " + nameWord + "at lines " + nameline.get(0) + " and " + nameline.get(1));
                System.out.println(seensofar); // Print all seen entries
            }
        }
    }
}
