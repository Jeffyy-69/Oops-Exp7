package oops_lab7;

import java.util.*;

class LengthException extends Exception {
    LengthException(String msg){
        super(msg);
    }
}

class FailedException extends Exception {
    FailedException(String msg){
        super(msg);
    }
}

class NotFirstClassException extends Exception {
    NotFirstClassException(String msg){
        super(msg);
    }
}

class Student {
    String name;
    int m1,m2,m3;

    Student(String name,int m1,int m2,int m3){
        this.name = name;
        this.m1 = m1;
        this.m2 = m2;
        this.m3 = m3;
    }

    void validate() throws LengthException,FailedException,NotFirstClassException {
        if(name.length() > 7){
            throw new LengthException("Name length greater than 7");
        }

        double avg = (m1+m2+m3)/3.0;

        if(avg < 50){
            throw new FailedException("Average < 50 , student failed");
        }

        if(avg < 75 && avg > 50){
            throw new NotFirstClassException("Avg between 50 and 75 , Not first class");
        }

        System.out.println("Student first class");
    }
}

public class StudentTest {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter Name: ");
        String name = sc.next();

        System.out.print("Enter 3 marks: ");
        int m1 = sc.nextInt();
        int m2 = sc.nextInt();
        int m3 = sc.nextInt();

        Student s = new Student(name,m1,m2,m3);

        try{
            s.validate();
        }
        catch(Exception e){
            System.out.println(e.getMessage());
        }
    }
}
