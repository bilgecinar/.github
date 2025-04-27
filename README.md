# Bilge Çınar: YouTube Video Quiz Generator

Bilge Çınar is a web application that allows users to automatically generate multiple-choice quizzes and summaries from YouTube videos. It is designed for educators, students, and anyone who wants to quickly create quizzes based on video content.

## Features

- **Automatic Quiz Generation:** Enter a YouTube video URL and generate 5 multiple-choice questions about the video.
- **Video Summary:** Get a concise summary of the video's main points.
- **Interactive Quiz UI:** Answer the generated questions directly in the app and see your score.
- **Daily Usage Limit:** Each user can generate up to 5 quizzes per day.
- **Responsive Design:** Clean, user-friendly interface that works on desktop and mobile.
- **Error Handling:** User-friendly error messages for invalid input, API errors, and daily limit reached.

---

## How It Works

1. **Input:** The user enters a YouTube video URL.
2. **Processing:** The app sends the video URL to the backend service, which uses the Gemini API to analyze the video and generate a summary and quiz.
3. **Output:** The app displays the video, the summary, and the quiz. Users can answer the quiz and see their results.

---

## Project Structure

```
src/
  app/
    app.component.html   // Main UI template
    app.component.ts     // Main UI logic
    services/
      gemini.service.ts  // Quiz generation and API logic
```

---

## UI Overview (`app.component.html`)

- **Header:** Project title and description.
- **Input Section:** Field to enter a YouTube video URL and a button to generate a quiz.
- **Remaining Quizzes:** Shows how many quizzes the user can generate today.
- **Video Preview:** Embeds the YouTube video for reference.
- **Summary Section:** Displays the generated summary of the video.
- **Quiz Section:** Shows the generated questions and options. Users can select answers and see their score after submission.
- **Error Handling:** Displays error messages for invalid input, API errors, or if the daily limit is reached.

---

## Main Logic (`app.component.ts`)

- **State Management:** Tracks the video URL, quiz questions, summary, user answers, loading state, errors, and score.
- **Quiz Generation:** Calls the `VideoQuizService` to generate a quiz and summary from the provided video URL.
- **Video Embedding:** Extracts the YouTube video ID and safely embeds the video.
- **Answer Selection:** Allows users to select answers for each question.
- **Quiz Submission:** Calculates and displays the user's score.
- **Visual Feedback:** Highlights correct and incorrect answers after submission.
- **Daily Limit:** Checks and displays the number of remaining quizzes for the day.

---

## Quiz Generation Service (`gemini.service.ts`)

- **API Integration:** Sends a request to the Gemini API with the video URL and a prompt to generate a summary and quiz.
- **Response Parsing:** Extracts and validates the summary and quiz from the API response.
- **Daily Limit Tracking:** Uses local storage to enforce a daily limit of 5 quizzes per user.
- **Error Handling:** Handles API errors and unsuitable video content gracefully.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd <your-repo-directory>
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up API Key

- Replace the placeholder API key in `src/app/services/gemini.service.ts` with your own Google Gemini API key.

### 4. Run the Application

```bash
ng serve
```

- Open your browser and go to `http://localhost:4200`.

---

## Usage

1. Enter a YouTube video URL in the input field.
2. Click "Quiz Oluştur" to generate a quiz and summary.
3. Watch the video, read the summary, and answer the quiz questions.
4. Submit your answers to see your score and which answers were correct.

---

## Example

**Input:**  
`https://www.youtube.com/watch?v=dQw4w9WgXcQ`

**Output:**  
- Embedded video player
- Short summary of the video
- 5 multiple-choice questions with 4 options each
- Score and feedback after submitting answers

---

## Response Format

The quiz service returns:

```json
{
  "summary": "Short summary of the video.",
  "quiz": [
    {
      "question": "Question text",
      "options": ["Option 1", "Option 2", "Option 3", "Option 4"],
      "correctAnswer": 2
    }
    // ...4 more questions
  ]
}
```

If the video is not suitable for quiz generation, the summary will contain:
```
"Bu video, test soruları hazırlamak için uygun değil."
```

---

## Contributing

Contributions are welcome! Please open issues or submit pull requests for improvements and bug fixes.

---

## License

[MIT](LICENSE)
