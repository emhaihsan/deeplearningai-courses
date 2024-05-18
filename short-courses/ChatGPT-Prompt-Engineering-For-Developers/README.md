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

# 3. Iterative Prompt Development
The instructor discusses the iterative process of developing prompts for large language models (LLMs) in application development. They emphasize that the first attempt rarely results in the final prompt, much like the initial training of a machine learning model. The process involves refining prompts through trial and error until achieving the desired outcome.

The instructor illustrates this with an example of creating a product description from a technical fact sheet for a chair. The initial prompt generates a detailed but lengthy description, leading to subsequent refinements specifying word count and target audience. Each iteration improves the prompt's effectiveness in conveying the necessary information concisely.

Key points include:
1. **Iterative Development**: Prompt creation is an ongoing process of testing and refinement.
2. **Example Workflow**: Starting with a basic prompt, the speaker demonstrates how to adjust length and focus based on feedback.
3. **Best Practices**: Emphasizing clarity, specificity, and giving the model time to think.
4. **Complex Prompts**: Adding detailed instructions like formatting output as HTML or including specific product IDs.
5. **Application Maturity**: Early development involves simple examples, while mature applications may require testing against multiple examples to fine-tune prompts.

# 4. Summarizing
The Instructor discusses the application of large language models (LLMs) for summarizing text. Key points include:

1. **Need for Summarization:** With an overwhelming amount of text available, summarization helps manage information efficiently.
2. **Use Case:** Summarizing product reviews on e-commerce sites to quickly grasp customer feedback.
3. **Practical Example:** Demonstrates summarizing a product review of a panda plush toy using a prompt to generate a concise summary.
4. **Custom Summaries:** Shows how to tailor summaries for specific departments, such as shipping or pricing, by modifying the prompt to focus on relevant details.
5. **Extraction of Information:** Illustrates extracting specific information instead of general summaries.
6. **Workflow Integration:** Presents a method to summarize multiple reviews, making it easier to read and analyze large volumes of customer feedback quickly.
7. **Efficiency:** Summarization helps in efficiently understanding customer sentiments and feedback without reading lengthy reviews.

Summarization can greatly aid in quickly understanding large amounts of text and provides practical examples and techniques to implement it effectively.

# 5. Inferring
The Instructor explains how to use large language models (LLMs) for making inferences from text, which includes tasks such as extracting sentiment, identifying emotions, and extracting specific information. Key points include:

1. **Simplified Process:** Traditional machine learning for tasks like sentiment analysis requires labeled datasets and model training. LLMs simplify this by allowing the creation of prompts to generate results immediately.
2. **Example Tasks:** The Instructor demonstrates several tasks using product reviews:
   - **Sentiment Analysis:** Determining if a review is positive or negative.
   - **Emotion Extraction:** Identifying emotions expressed in a review.
   - **Specific Information Extraction:** Extracting details such as item names and brands.
3. **Prompt Customization:** Shows how to customize prompts for different purposes and how a single prompt can be used to extract multiple pieces of information simultaneously.
4. **Topic Inference:** Demonstrates using prompts to infer topics from a piece of text and how this can be applied to a news website to categorize articles.
5. **Zero-Shot Learning:** Highlights the capability of LLMs to perform tasks without needing labeled training data, making the development process faster and more efficient.
6. **Practical Applications:** Discusses potential applications, such as generating news alerts based on inferred topics from articles.

Overall, the video showcases the versatility and efficiency of LLMs in performing various natural language processing tasks through simple prompting.

# 6. Transforming
The Instructor explains how large language models (LLMs) excel at transforming text, highlighting various applications:

1. **Translation:** LLMs can translate text between multiple languages, handle formal and informal tones, and identify the language of a given text.
2. **Format Conversion:** They can convert text formats, such as JSON to HTML, enabling easier manipulation and display of data.
3. **Grammar and Spelling Correction:** LLMs can proofread and correct text, making it useful for non-native speakers or those wanting to ensure grammatical accuracy.
4. **Tone Transformation:** They can change the tone of a text to suit different audiences, such as converting slang to formal business language.
5. **Example Demonstrations:**
   - **Translation Task:** Translates English to Spanish and identifies French text.
   - **Universal Translator:** Handles multiple languages, translating user messages into English and Korean.
   - **Tone and Format Conversion:** Transforms informal text into formal business letters and JSON data into HTML tables.
   - **Grammar and Spelling Check:** Corrects grammatical errors in sentences and checks text before posting in public forums.
   - **Compelling Text and APA Style:** Enhances a product review to make it more compelling and adheres to APA style, outputting in markdown format.

# 7. Expanding
The video discusses the concept of "expanding," which involves using large language models (LLMs) to generate longer texts from shorter inputs, such as turning a list of topics into an essay or creating personalized emails. Key points include:

1. **Applications of Expanding:** LLMs can generate emails, essays, or other extended texts from brief prompts. This capability can be used for brainstorming but also has potential misuse, such as generating spam.
2. **Responsible Use:** It’s important to use LLMs responsibly and transparently, especially when generating text for users, by indicating that the text is AI-generated.
3. **Example:** The video demonstrates generating a custom email response to a customer review. The model uses the review's sentiment to tailor the response appropriately, thanking the customer for positive or neutral feedback or apologizing for negative feedback and suggesting they contact customer service.
4. **Temperature Parameter:** The temperature setting in LLMs controls the randomness of the generated text. A lower temperature (e.g., 0) yields more predictable outputs, while a higher temperature (e.g., 0.7) produces more varied and creative responses. The video includes examples showing how varying the temperature affects the generated emails.
5. **Experimentation:** Users are encouraged to experiment with different temperatures to observe the variation in outputs.

# 8. Chatbot
The video explains how to build a custom chatbot using a large language model, specifically utilizing OpenAI's chat completions format. Here are the key points:

1. **Introduction to Chatbots:** Large language models like ChatGPT can be used to create custom chatbots for roles such as AI customer service agents or order takers with minimal effort.

2. **Chat Completions Format:** These models are trained to take a series of messages as input and return a model-generated message as output, suitable for multi-turn conversations as well as single-turn tasks.

3. **Helper Functions:** The video introduces two helper functions: one for getting a single completion from a prompt and another for handling a list of messages from different roles (user, assistant, system).

4. **System Messages:** System messages set the behavior and persona of the assistant. They guide the assistant's responses without the user being aware of the system message.

5. **Examples:**
   - **Shakespearean Assistant:** A chatbot is programmed to speak like Shakespeare, demonstrating how system messages can influence the assistant's style.
   - **Friendly Chatbot:** A chatbot is set up to respond in a friendly manner, showing how the context must include all relevant information for accurate responses.

6. **Building OrderBot:**
   - **Function Setup:** The video demonstrates creating a helper function to automate collecting user messages and responses, appending them to a context list, and calling the model with this context.
   - **User Interaction:** An example conversation is shown where a user orders a pizza, and the chatbot follows the instructions given in the system message.
   - **Order Summary:** The chatbot generates a JSON summary of the order, which could be submitted to an order system.

7. **Customization:** Viewers are encouraged to customize the chatbot's behavior and persona by modifying the system message and experimenting with different setups.
