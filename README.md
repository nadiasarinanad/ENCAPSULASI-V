# ENCAPSULASI-V
    package com.mycompany.mavenproject6;
    
    import java.util.Arrays;
    
    class Person {
        private final String name;
        private String address;
    
        public Person(String name, String address) {
            this.name = name;
            this.address = address;
        }
    
        public String getName() {
            return name;
        }
    
        public String getAddress() {
            return address;
        }
    
        public void setAddress(String address) {
            this.address = address;
        }
    
        public String toString() {
            return name + " (" + address + ")";
        }
    }
    
    class Student extends Person {
        private int numCourses;
        private String[] courses;
        private int[] grades;
        
        public Student(String name, String address) {
            super(name, address);
            numCourses = 0;
            courses = new String[10]; // assuming a maximum of 10 courses
            grades = new int[10];
        }
    
        public void addCourseGrade(String course, int grade) {
            courses[numCourses] = course;
            grades[numCourses] = grade;
            numCourses++;
        }
    
        public void printGrades() {
            System.out.println(Arrays.toString(grades));
        }
    
        public double getAverageGrade() {
            if (numCourses == 0)
                return 0;
            
            int sum = 0;
            for (int grade : grades) {
                sum += grade;
            }
            return (double) sum / numCourses;
        }
    
        public String toString() {
            return "Student: " + super.toString();
        }
    }
    
    class Teacher extends Person {
        private int numCourses;
        private String[] courses;
    
        public Teacher(String name, String address) {
            super(name, address);
            numCourses = 0;
            courses = new String[10]; // assuming a maximum of 10 courses
        }
    
        public boolean addCourse(String course) {
            for (String c : courses) {
                if (c != null && c.equals(course))
                    return false; // course already exists
            }
            courses[numCourses] = course;
            numCourses++;
            return true;
        }
    
        public boolean removeCourse(String course) {
            for (int i = 0; i < numCourses; i++) {
                if (courses[i].equals(course)) {
                    courses[i] = null;
                    numCourses--;
                    return true;
                }
            }
            return false; // course not found
        }
    
        public String toString() {
            return "Teacher: " + super.toString();
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            // Example usage
            Student student = new Student("John Doe", "123 Main St");
            student.addCourseGrade("Math", 90);
            student.addCourseGrade("Science", 85);
            System.out.println(student);
            System.out.println("Average Grade: " + student.getAverageGrade());
            student.printGrades();
    
            Teacher teacher = new Teacher("Jane Smith", "456 Elm St");
            teacher.addCourse("Math");
            teacher.addCourse("Science");
            System.out.println(teacher);
        }
    }
