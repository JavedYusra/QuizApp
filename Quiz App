import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class QuizApp extends JFrame implements ActionListener {
    private String[] questions = {
        "What is the capital of France?",
        "What is the sum of 5 + 3?",
        "Which planet is known as the Red Planet?"
    };
    private String[][] options = {
        {"Berlin", "Madrid", "Paris", "Lisbon"},
        {"6", "7", "8", "9"},
        {"Earth", "Mars", "Jupiter", "Saturn"}
    };
    private int[] answers = {2, 2, 1}; // Correct option indices
    private int currentQuestion = 0, score = 0;

    private JLabel questionLabel;
    private JRadioButton[] optionButtons = new JRadioButton[4];
    private ButtonGroup optionsGroup;
    private JButton nextButton;

    public QuizApp() {
        setTitle("Quiz App");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        JPanel panel = new JPanel(new GridLayout(6, 1));
        questionLabel = new JLabel(questions[currentQuestion]);
        panel.add(questionLabel);

        optionsGroup = new ButtonGroup();
        for (int i = 0; i < 4; i++) {
            optionButtons[i] = new JRadioButton(options[currentQuestion][i]);
            optionsGroup.add(optionButtons[i]);
            panel.add(optionButtons[i]);
        }

        nextButton = new JButton("Next");
        nextButton.addActionListener(this);
        panel.add(nextButton);

        add(panel);
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        int selectedOption = -1;
        for (int i = 0; i < 4; i++) {
            if (optionButtons[i].isSelected()) {
                selectedOption = i;
                break;
            }
        }

        if (selectedOption == answers[currentQuestion]) {
            score++;
        }

        currentQuestion++;

        if (currentQuestion < questions.length) {
            updateQuestion();
        } else {
            showResults();
        }
    }

    private void updateQuestion() {
        optionsGroup.clearSelection();
        questionLabel.setText(questions[currentQuestion]);
        for (int i = 0; i < 4; i++) {
            optionButtons[i].setText(options[currentQuestion][i]);
        }
    }

    private void showResults() {
        JOptionPane.showMessageDialog(
            this,
            "Quiz Completed!\n" +
            "Score: " + score + " / " + questions.length,
            "Results",
            JOptionPane.INFORMATION_MESSAGE
        );
        System.exit(0);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(QuizApp::new);
    }
}
