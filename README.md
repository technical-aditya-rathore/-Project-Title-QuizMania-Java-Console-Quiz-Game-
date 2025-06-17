# -Project-Title-QuizMania-Java-Console-Quiz-Game-
🎯 Objective: Create a console-based Java quiz app that:  Loads multiple-choice questions  Lets the user play a quiz game  Tracks and displays the final score  Optionally stores top score in a file (high score)
_______________________________________________+++++++++++++++++++++++++++++++++____________________________________________________________________________________________


---

## 💡 Project Title: **"QuizMania – Java Console Quiz Game"**

---

## 🎯 Objective:

Create a **console-based Java quiz app** that:

* Loads multiple-choice questions
* Lets the user play a quiz game
* Tracks and displays the final score
* Optionally stores top score in a file (high score)

---

## 📁 File Structure:

```
QuizMania/
│
├── Question.java
├── QuizGame.java
└── Main.java
```

---

## 🔹 `Question.java` – Model Class

```java
public class Question {
    String questionText;
    String[] options;
    int correctOption;

    public Question(String questionText, String[] options, int correctOption) {
        this.questionText = questionText;
        this.options = options;
        this.correctOption = correctOption;
    }

    public boolean isCorrect(int answer) {
        return answer == correctOption;
    }

    public void displayQuestion() {
        System.out.println("\n" + questionText);
        for (int i = 0; i < options.length; i++) {
            System.out.println((i + 1) + ". " + options[i]);
        }
    }
}
```

---

## 🔹 `QuizGame.java` – Core Logic

```java
import java.util.*;

public class QuizGame {
    private List<Question> questions;
    private int score;

    public QuizGame() {
        questions = new ArrayList<>();
        score = 0;
        loadQuestions();
    }

    private void loadQuestions() {
        questions.add(new Question("Which language is used for Android development?",
                new String[]{"Python", "Java", "Swift", "C++"}, 2));
        questions.add(new Question("What does HTML stand for?",
                new String[]{"Hyper Text Markup Language", "HighText Machine Language", "Hyper Terminal Mail Language", "None"}, 1));
        questions.add(new Question("Who is the founder of Microsoft?",
                new String[]{"Steve Jobs", "Elon Musk", "Bill Gates", "Mark Zuckerberg"}, 3));
        questions.add(new Question("Which of the following is not an OOP concept?",
                new String[]{"Encapsulation", "Abstraction", "Polymorphism", "Compilation"}, 4));
        questions.add(new Question("Which keyword is used to inherit a class in Java?",
                new String[]{"this", "super", "extends", "implements"}, 3));
    }

    public void startQuiz() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("🧠 Welcome to QuizMania!");
        System.out.println("---------------------------");

        for (Question q : questions) {
            q.displayQuestion();
            System.out.print("Your answer (1-4): ");
            int ans = scanner.nextInt();

            if (q.isCorrect(ans)) {
                System.out.println("✅ Correct!");
                score++;
            } else {
                System.out.println("❌ Wrong. Correct Answer: " + q.options[q.correctOption - 1]);
            }
        }

        System.out.println("\n🎯 Quiz Over! Your Score: " + score + "/" + questions.size());

        if (score == questions.size()) {
            System.out.println("🏆 Perfect Score! You're a genius!");
        } else if (score >= 3) {
            System.out.println("👏 Good job! Keep it up.");
        } else {
            System.out.println("💡 Keep learning and try again!");
        }

        scanner.close();
    }
}
```

---

## 🔹 `Main.java` – Game Launcher

```java
public class Main {
    public static void main(String[] args) {
        QuizGame game = new QuizGame();
        game.startQuiz();
    }
}
```

---

## 🚀 How to Run:

1. Save all 3 files in a folder `QuizMania`
2. Compile:

   ```bash
   javac *.java
   ```
3. Run:

   ```bash
   java Main
   ```

---

## 🌈 Optional Features You Can Add:

* High score file saving (using `FileWriter`)
* Timed quiz (using `Timer`)
* Random question order (using `Collections.shuffle`)
* GUI version with Swing

---

ADITYA KUMAR JHA (OWNED)

