# 1. Introduction
Discuss the two main types of LLMs (Large Language Models) and best practices for using them in software development.

* **Base LLMs** are trained to predict the next word based on a massive dataset of text and code. 
* **Instruction-tuned LLMs** are trained to follow instructions and are generally better suited for practical applications.

The course will focus on prompting best practices for instruction-tuned LLMs. Here are some key takeaways:

* Provide clear and specific instructions to the LLM. 
* Consider the desired tone (professional, casual, etc.) of the LLM's output.
* Imagine instructing a recent college graduate to complete the task. Provide them with any relevant background information if possible.
* The course will cover examples of clear and specific prompts, and the importance of giving the LLM time to process.

# 2. Guidelines
This lecture about prompting techniques for large language models like ChatGPT. The instructor outlines two key principles for effective prompting:

1. **Write clear and specific instructions:**
   - Provide instructions that are clear and specific to avoid irrelevant or incorrect responses.
   - Use delimiters to indicate distinct parts of the input (e.g., triple backticks for text to be summarized).
   - Ask for structured outputs (e.g., JSON) for easier parsing.
   - Consider potential edge cases and how the model should handle them.
   - Use few-shot prompting (providing examples) to guide the model towards the desired response.

2. **Give the model time to think:**
   - If the model makes reasoning errors, try reframing the query to request a series of steps before the final answer.
   - Complex tasks might require the model to think longer. You can instruct the model to do so for improved results.
