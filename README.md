# Student-report-java-project-
Java project 
public class Student {

    // variables to store student data
    private String name;
    private int mark1;
    private int mark2;
    private int mark3;

    // constructor - runs when you create a new Student
    public Student(String name, int mark1, int mark2, int mark3) {
        this.name  = name;
        this.mark1 = mark1;
        this.mark2 = mark2;
        this.mark3 = mark3;
    }

    // getters - to read private data
    public String getName()  { return name; }
    public int getMark1()    { return mark1; }
    public int getMark2()    { return mark2; }
    public int getMark3()    { return mark3; }

    // calculate average of 3 marks
    public double getAverage() {
        return (mark1 + mark2 + mark3) / 3.0;
    }

    // find which subject has highest mark
    public int getHighest() {
        return Math.max(mark1, Math.max(mark2, mark3));
    }

    // find which subject has lowest mark
    public int getLowest() {
        return Math.min(mark1, Math.min(mark2, mark3));
    }
}
public class ReportCard {

    // this method takes a Student and prints their report
    public void printReport(Student s) {

        System.out.println("==============================");
        System.out.println("       STUDENT REPORT CARD    ");
        System.out.println("==============================");
        System.out.println("Name    : " + s.getName());
        System.out.println("Mark 1  : " + s.getMark1());
        System.out.println("Mark 2  : " + s.getMark2());
        System.out.println("Mark 3  : " + s.getMark3());
        System.out.println("------------------------------");
        System.out.printf ("Average : %.2f%n", s.getAverage());
        System.out.println("Highest : " + s.getHighest());
        System.out.println("Lowest  : " + s.getLowest());
        System.out.println("Grade   : " + getGrade(s.getAverage()));
        System.out.println("Result  : " + getResult(s));
        System.out.println("==============================");
    }

    // give grade based on average
    private String getGrade(double avg) {
        if (avg >= 90)      return "A+";
        else if (avg >= 75) return "A";
        else if (avg >= 60) return "B";
        else if (avg >= 50) return "C";
        else                return "F";
    }

    // pass only if all 3 marks are 35 or above
    private String getResult(Student s) {
        if (s.getMark1() >= 35
         && s.getMark2() >= 35
         && s.getMark3() >= 35) {
            return "PASS ✓";
        } else {
            return "FAIL ✗";
        }
    }
}
import java.util.Scanner;

public class MainApp {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter student name : ");
        String name = sc.nextLine();

        System.out.println("Enter mark 1 : ");
        int m1 = sc.nextInt();

        System.out.println("Enter mark 2 : ");
        int m2 = sc.nextInt();

        System.out.println("Enter mark 3 : ");
        int m3 = sc.nextInt();

        // create Student object with the entered data
        Student student = new Student(name, m1, m2, m3);

        // create ReportCard object and print
        ReportCard card = new ReportCard();
        card.printReport(student);

        sc.close();
    }
}
```

### Line by line:
- `Scanner sc` → reads keyboard input
- `sc.nextLine()` → reads a full line of text
- `sc.nextInt()` → reads a number
- `new Student(...)` → creates Student object → calls constructor
- `new ReportCard()` → creates ReportCard object
- `card.printReport(student)` → calls the method, passes student in

---

## Output You'll See
```
Enter student name :
Rahul
Enter mark 1 :
85
Enter mark 2 :
72
Enter mark 3 :
90

==============================
       STUDENT REPORT CARD
==============================
Name    : Rahul
Mark 1  : 85
Mark 2  : 72
Mark 3  : 90
------------------------------
Average : 82.33
Highest : 90
Lowest  : 72
Grade   : A
Result  : PASS ✓
==============================
