# Project: Quiz Master

A client-side quiz application where users can test their knowledge on various topics.

---

## Goal

Build a single-page React application that allows users to take quizzes, track their score, and review their answers. The app stores quiz data locally (in code or localStorage) and doesn't require a backend.

---

## Tech Stack

- **Runtime**: Bun
- **Front-end**: React + Vite
- **Styling**: Tailwind CSS (recommended)
- **State Management**: React built-in state (useState, useContext)

---

## Difficulty

**Beginner** - Suitable for junior developers

### Concepts You Should Know

- JavaScript fundamentals (functions, arrays, objects, async/await)
- React basics (components, props, state, hooks)
- React hooks (useState, useEffect, useContext)
- Conditional rendering
- List rendering with keys
- Basic CSS and responsive design
- Git basics (commits, branches)

---

## Features & User Stories

### 1. Quiz Selection

**As a user**, I want to select a quiz topic so I can test my knowledge.

**Acceptance Criteria:**
- Display a list of available quizzes (at least 3 topics)
- Each quiz card shows title, description, and number of questions
- Clicking a quiz starts the quiz

### 2. Taking a Quiz

**As a user**, I want to answer questions one at a time so I can focus on each question.

**Acceptance Criteria:**
- Display one question at a time with multiple choice answers (4 options)
- Show current question number and total (e.g., "Question 3 of 10")
- Show a progress bar
- User can select an answer and proceed to next question
- User cannot go back to previous questions (to keep it simple)

### 3. Answer Feedback

**As a user**, I want immediate feedback on my answer so I know if I was correct.

**Acceptance Criteria:**
- After selecting an answer, show if it was correct or wrong
- Highlight correct answer in green, wrong answer in red
- Show a "Next Question" button after answering
- Brief delay (or button click) before moving to next question

### 4. Quiz Results

**As a user**, I want to see my final score so I can know how well I did.

**Acceptance Criteria:**
- Display total score (e.g., "7 out of 10")
- Display percentage score
- Show a message based on score (e.g., "Great job!", "Keep practicing!")
- Option to retry the quiz or go back to quiz selection

### 5. Answer Review

**As a user**, I want to review my answers after completing a quiz so I can learn from mistakes.

**Acceptance Criteria:**
- Show a list of all questions with user's answers
- Indicate which answers were correct/incorrect
- Show the correct answer for wrong responses

### 6. Score History (Optional Bonus)

**As a user**, I want to see my past quiz attempts so I can track my progress.

**Acceptance Criteria:**
- Store quiz results in localStorage
- Display history of attempts with date, quiz name, and score
- Option to clear history

---

## Development Guidelines

### Project Structure

```
quiz-master/
├── public/
├── src/
│   ├── components/       # Reusable UI components
│   ├── pages/            # Page components (Home, Quiz, Results)
│   ├── data/             # Quiz data (JSON or JS objects)
│   ├── context/          # React context for quiz state
│   ├── hooks/            # Custom hooks
│   └── App.jsx
├── package.json
└── README.md
```

### Guidelines

1. **Component Organization**
   - Create small, reusable components (Button, Card, ProgressBar, etc.)
   - Keep components focused on a single responsibility
   - Use props for component configuration

2. **State Management**
   - Use `useState` for local component state
   - Use `useContext` for global quiz state (current quiz, score, answers)
   - Create a `QuizContext` to share state across components

3. **Data Structure**
   - Store quiz data as JavaScript objects or JSON files
   - Each quiz should have: id, title, description, questions array
   - Each question should have: id, question text, options array, correct answer index

4. **Code Quality**
   - Use meaningful variable and function names
   - Add comments for complex logic
   - Keep functions small and focused

5. **Styling**
   - Make the app responsive (works on mobile and desktop)
   - Use consistent spacing and colors
   - Add hover states for interactive elements

### Example Quiz Data Structure

```javascript
const quiz = {
  id: "javascript-basics",
  title: "JavaScript Basics",
  description: "Test your knowledge of JavaScript fundamentals",
  questions: [
    {
      id: 1,
      question: "What keyword is used to declare a variable in modern JavaScript?",
      options: ["var", "let", "const", "Both let and const"],
      correctIndex: 3
    },
    // ... more questions
  ]
};
```

---

## Getting Started

1. Create the React app with Vite (`bun create vite`)
2. Set up Tailwind CSS
3. Set up basic routing (can use simple state-based routing, no need for react-router)
4. Create the quiz data
5. Build components incrementally
6. Test on different screen sizes

---

## Stretch Goals (If You Have Extra Time)

- Add a timer for each question
- Add difficulty levels (easy, medium, hard)
- Add animations/transitions between questions
- Add sound effects for correct/wrong answers
- Allow users to create their own quizzes (stored in localStorage)
