🧮 Calculator App (Java Swing GUI)
📖 Project Overview

This is a simple yet fully functional Calculator Application built using Java Swing.
It allows users to perform basic arithmetic operations such as addition, subtraction, multiplication, and division through an interactive GUI.

This project demonstrates core Java concepts, event-driven programming, and Swing-based GUI design — making it ideal for learning and portfolio purposes.

🧠 Features

✅ User-friendly GUI interface
✅ Supports +, -, ×, ÷ operations
✅ Displays input and result in real-time
✅ Handles division by zero with an error message
✅ Clear (C) button to reset input

⚙️ Technologies Used
Component	Technology
Language	Java (JDK 8+)
GUI Framework	Java Swing
IDE (optional)	VS Code / IntelliJ / Eclipse
💻 Code Structure

📁 CalculatorApp.java

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class CalculatorApp extends JFrame implements ActionListener {
    private JTextField display;
    private double num1 = 0, num2 = 0, result = 0;
    private char operator;

    public CalculatorApp() {
        setTitle("Calculator App");
        setSize(350, 450);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        display = new JTextField();
        display.setEditable(false);
        display.setFont(new Font("Arial", Font.BOLD, 24));
        add(display, BorderLayout.NORTH);

        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(4, 4, 10, 10));

        String[] buttons = {
                "7", "8", "9", "/",
                "4", "5", "6", "*",
                "1", "2", "3", "-",
                "0", "C", "=", "+"
        };

        for (String text : buttons) {
            JButton button = new JButton(text);
            button.setFont(new Font("Arial", Font.BOLD, 20));
            button.addActionListener(this);
            panel.add(button);
        }

        add(panel, BorderLayout.CENTER);
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        String command = e.getActionCommand();

        if (Character.isDigit(command.charAt(0))) {
            display.setText(display.getText() + command);
        } else if (command.equals("C")) {
            display.setText("");
            num1 = num2 = result = 0;
        } else if (command.equals("=")) {
            try {
                num2 = Double.parseDouble(display.getText());
                switch (operator) {
                    case '+': result = num1 + num2; break;
                    case '-': result = num1 - num2; break;
                    case '*': result = num1 * num2; break;
                    case '/':
                        if (num2 != 0) result = num1 / num2;
                        else JOptionPane.showMessageDialog(this, "Cannot divide by zero");
                        break;
                }
                display.setText(String.valueOf(result));
            } catch (Exception ex) {
                JOptionPane.showMessageDialog(this, "Invalid input");
            }
        } else {
            try {
                num1 = Double.parseDouble(display.getText());
                operator = command.charAt(0);
                display.setText("");
            } catch (Exception ex) {
                JOptionPane.showMessageDialog(this, "Enter a valid number first");
            }
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(CalculatorApp::new);
    }
}

▶️ How to Run the Project
🧱 Compile
javac CalculatorApp.java

▶️ Run
java CalculatorApp


A calculator window will appear on your screen.

🧩 Example Output

Interface Layout:

+---------------------------+
|        [Display]          |
|---------------------------|
| 7 | 8 | 9 | /             |
| 4 | 5 | 6 | *             |
| 1 | 2 | 3 | -             |
| 0 | C | = | +             |
+---------------------------+


Example:

Input: 8 + 2 =
Output: 10

📷 (Optional) Add Screenshots

You can add a screenshot of your calculator GUI here for your GitHub README:

<img width="497" height="654" alt="image" src="https://github.com/user-attachments/assets/7364924d-8fb8-410f-b7b5-2bab744724b0" />


🧑‍💻 Author

P.Srikesh
B.Tech CSE, SRM Institute of Science and Technology
📍 Kattankulathur

GitHub: https://github.com/srikesh-10

🏁 Project Status

✅ Completed and Working
🔹 Simple GUI-based Java project for beginners
🔹 Can be extended to include scientific operations
