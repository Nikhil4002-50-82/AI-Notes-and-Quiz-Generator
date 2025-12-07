# Automated Notes and Quiz Generator using LangChain and HuggingFace

## Overview

This project implements an automated pipeline that analyzes any given text, extracts key concepts as notes, and generates five quiz questions along with their corresponding answers. The system is built using LangChain, HuggingFace Inference Endpoints, and Pydantic models for structured output.

The workflow uses a parallel execution design where notes and quizzes are generated simultaneously using `RunnableParallel`. The final output is formatted into a clean, structured summary.

## Features

* Extracts key concepts from input text without modifying the original wording.
* Generates five quiz questions strictly based on the input text.
* Produces structured quiz objects using Pydantic models.
* Uses HuggingFace's `openai/gpt-oss-20b` model through LangChain.
* Combines parallel chains to optimise performance.
* Outputs final results in a neat, readable format.

## Technologies Used

* **Python**
* **LangChain**

  * ChatHuggingFace
  * PromptTemplate
  * RunnableParallel
  * Output Parsers
* **HuggingFace Inference API**
* **Pydantic** (for structured output models)

## How It Works

1. **Input Text**
   User provides raw text for analysis.

2. **Notes Extraction Chain**
   A prompt analyzes the text and extracts important concepts using exact wording from the input.

3. **Quiz Generation Chain**
   A separate prompt generates five quiz questions and answers.
   Structure is enforced using Pydantic (`Quiz` and `QuizSet` models).

4. **Parallel Execution**
   Both chains run simultaneously using `RunnableParallel`.

5. **Final Formatting**
   Output is passed to a final template to produce a clean summary containing:

   * Notes
   * Quiz Questions and Answers

## Output Format

The final output includes:

```
----------------------------------
NOTES-
----------------------------------
<Extracted notes>

----------------------------------
QUIZ QUESTIONS and ANSWERS-
----------------------------------
<Quiz Q&A in structured format>
```

## Use Cases

* Automated content summarization
* Educational content generation
* Study material preparation
* AI-driven question generation
* NLP experimentation with structured outputs

## Future Improvements

* Support for multiple quiz difficulty levels
* Optional paraphrasing allowed mode
* PDF export of notes and quizzes
* Streamlit UI for interactive use
* Support for more LLM backends (Gemini, GPT-4, LLaMA)
