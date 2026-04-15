package hospital;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
// Base Class (Inheritance)
class Person {
String name;
int age;
Person(String name, int age) {
this.name = name;
this.age = age;
}
}
// Patient Class (Encapsulation + Inheritance)
class Patient extends Person {
String id;
Patient(String name, int age, String id) {
super(name, age);
this.id = id;
}
String getInfo() {
return name + "," + age + "," + id;
}
}
// Appointment Class
class Appointment {
String doctor;
String date;
Appointment(String doctor, String date) {
this.doctor = doctor;
this.date = date;
}
String getInfo() {
return doctor + "," + date;
}
}
// Polymorphism (File Saving)
class FileManager {
void save(String data) throws IOException {
System.out.println("Saving...");
}
}
class PatientFileManager extends FileManager {
@Override
void save(String data) throws IOException {
FileWriter fw = new FileWriter("patients.txt", true);
fw.write(data + "\n");
fw.close();
}
}
// GUI Class
public class HospitalSystem extends JFrame {
JTextField nameF, ageF, idF, docF, dateF;
JTextArea area;
public HospitalSystem() {
setTitle("Hospital System");
setSize(400, 400);
setLayout(new FlowLayout());
setDefaultCloseOperation(EXIT_ON_CLOSE);
add(new JLabel("Name"));
nameF = new JTextField(10);
add(nameF);
add(new JLabel("Age"));
ageF = new JTextField(5);
add(ageF);
add(new JLabel("ID"));
idF = new JTextField(8);
add(idF);
add(new JLabel("Doctor"));
docF = new JTextField(10);
add(docF);
add(new JLabel("Date"));
dateF = new JTextField(10);
add(dateF);
JButton regBtn = new JButton("Register");
JButton apptBtn = new JButton("Appointment");
add(regBtn);
add(apptBtn);
area = new JTextArea(10, 30);
add(area);
// Register Patient
regBtn.addActionListener(e -> {
try {
Patient p = new Patient(
nameF.getText(),
Integer.parseInt(ageF.getText()),
idF.getText()
);
PatientFileManager fm = new PatientFileManager();
fm.save(p.getInfo());
area.append("Patient Added: " + p.getInfo() + "\n");
} catch (Exception ex) {
JOptionPane.showMessageDialog(this, "Error in Input!");
}
});
// Appointment
apptBtn.addActionListener(e -> {
try {
Appointment a = new Appointment(
docF.getText(),
dateF.getText()
);
FileWriter fw = new FileWriter("appointments.txt", true);
fw.write(a.getInfo() + "\n");
fw.close();
area.append("Appointment: " + a.getInfo() + "\n");
} catch (Exception ex) {
JOptionPane.showMessageDialog(this, "File Error!");
}
});
}
public static void main(String[] args) {
new HospitalSystem().setVisible(true);
}
}
