# 0. Introduction
The video introduces the course on building systems using the ChatGPT API. It highlights that creating a system involves more than a single prompt or API call and aims to teach best practices for developing complex applications with large language models (LLMs). The course uses the example of an end-to-end customer service assistant that handles multiple steps, such as evaluating user input, identifying query types, retrieving relevant information, generating responses, and checking outputs for issues.

Key themes include:

1. **Multi-Step Processing**: Systems often require multiple internal steps to process user input before producing the final output.
2. **Continuous Improvement**: Emphasis on developing, evaluating, and improving LLM-based applications over time.
3. **Collaboration**: Acknowledgment of contributions from the OpenAI and DeepLearning.AI teams.

The course aims to equip learners with the skills to build and maintain complex, multi-step applications using LLMs.

# 1. Language Models, the Chat Format and Tokens
The video provides an overview of how Large Language Models (LLMs) work and how to use them. It covers the following key points:

1. **Training LLMs**: LLMs are trained using supervised learning to predict the next word in a sequence. This involves using a vast amount of text data to create training sets where the model learns to predict the next word given a sentence fragment.

2. **Types of LLMs**: There are two main types of LLMs: Base LLMs and Instruction Tuned LLMs. Base LLMs predict the next word based on text data, while Instruction Tuned LLMs are further trained to follow specific instructions.

3. **Fine-Tuning**: After training a Base LLM, it is fine-tuned with examples of instructions and good responses. This process can be enhanced with human feedback to improve the quality of the LLM's output.

4. **Tokenization**: LLMs predict the next token, not the next word. Tokens are sequences of characters that frequently appear together. This tokenization affects how LLMs process and generate text, and can be manipulated to improve performance on specific tasks.

5. **Using the Chat Format**: The chat format allows specifying system, user, and assistant messages to control the behavior and responses of the LLM. System messages set the overall tone, while user messages provide specific instructions.

6. **Security Practices**: For secure API usage, it's recommended to store API keys in environment variables using libraries like `dotenv` instead of hardcoding them in code.

7. **Efficiency of Prompting**: Prompting-based machine learning can significantly speed up the development process compared to traditional supervised learning. This method is particularly effective for unstructured data applications, such as text.

The video also demonstrates practical examples, including a helper function to get a completion from multiple messages, and emphasizes the importance of evaluating and improving LLMs over time.

# 2. Classification
The video focuses on evaluating inputs to ensure system quality and safety, particularly for customer service assistants. Key points include:

1. **Classifying Queries**: It's beneficial to first classify the type of query and then use specific instructions based on that classification. This involves defining fixed categories and hard-coding relevant instructions for each category.

2. **Example Scenarios**: For instance, different instructions are given if a user wants to close their account versus asking about a specific product. Additional instructions about closing the account or providing product information would be used accordingly.

3. **System Message and Delimiters**: The system message instructs the model to classify customer service queries into primary and secondary categories using delimiters (hashtags) to separate different parts of the instruction.

4. **Structured Output**: The model provides the classification output in a JSON format, which can be easily read into an object like a dictionary in Python. This structured output can be used as input for subsequent steps.

5. **Examples**: 
   - User message: "I want you to delete my profile and all of my user data." 
   - Model classifies it as account management (primary) and close account (secondary).

   - User message: "Tell me more about your flat screen TVs."
   - Model classifies it as product inquiry (primary) and flat screen TVs (secondary).

6. **Specific Instructions Based on Classification**: Based on the categorization, more specific instructions can be provided to handle the next steps. For instance, additional TV information for product inquiries or a link to close the account for account management queries.

# 3. Moderation
The video explains strategies for ensuring the responsible use of AI systems by moderating user inputs. Key points include:

1. **Moderation API**:
   - OpenAI’s Moderation API helps ensure content compliance with usage policies, identifying and filtering prohibited content (hate, self-harm, sexual, and violence).
   - Example: Using `openai.Moderation.create` to flag inappropriate content, displaying category-specific scores and overall harmfulness.

2. **Prompt Injections**:
   - Users might try to manipulate the AI by injecting prompts that override or bypass developer-set instructions.
   - Strategies to avoid this include using delimiters and clear instructions in the system message, and asking if a user is attempting a prompt injection.

3. **Example Scenarios**:
   - Demonstrated removing delimiters from user messages to avoid confusion.
   - Example with system messages: Ensuring responses are in a specific language, regardless of user attempts to change the instructions.
   - Checking user messages for potential prompt injections using clear Y/N responses based on whether the user tries to override instructions.

4. **Advanced Models**:
   - More advanced models like GPT-4 are better at following complex instructions and avoiding prompt injections.

# 4. Reasoning
The transcript discusses strategies for processing inputs in AI systems, focusing on detailed reasoning and structured output methods. Key points include:

1. **Chain of Thought Reasoning**:
   - Encourages the model to think through a series of steps before providing a final answer, improving accuracy and reducing errors.
   - This approach helps the model reason in detail about a problem before answering.

2. **Inner Monologue**:
   - A technique where the model's reasoning process is hidden from the user.
   - This involves structuring the output to make it easy to separate the reasoning steps from the final answer visible to the user.

3. **Example Scenario**:
   - A customer query is processed using specific steps, including identifying if the query is about a specific product, listing user assumptions, verifying these assumptions, and correcting any incorrect assumptions.
   - The reasoning steps are separated using delimiters to facilitate easy parsing and presentation of the final response to the user.

4. **Handling User Queries**:
   - Examples demonstrate how the model processes queries, identifies incorrect assumptions, and provides polite corrections.
   - The model is guided to think longer and more methodically, similar to human reasoning.

5. **Advanced Models**:
   - More advanced models like GPT-4 can handle complex instructions better and follow specific formats more accurately.

6. **Optimization and Experimentation**:
   - Experimentation is encouraged to find the optimal balance in prompt complexity.
   - Trying different prompts helps in determining the most effective approach for specific tasks.

# 5. Chaining Prompts
The video covers strategies for handling complex tasks by breaking them down into simpler subtasks through chaining multiple prompts. Key points include:

1. **Chaining Prompts**:
   - Splitting complex tasks into a series of simpler subtasks can make the process more manageable and reduce errors.
   - This approach is compared to cooking a complex meal in stages versus all at once, or modular programming versus spaghetti code.

2. **Advantages of Chaining**:
   - Easier to manage the state of the system at any given point.
   - Each subtask contains only the necessary instructions for its state, making the system more efficient and reducing the likelihood of errors.
   - Can reduce costs as longer prompts with more tokens are more expensive to run.
   - Easier to test and identify failing steps, and to involve a human in the loop at specific steps.

3. **Example Workflow**:
   - An example is provided where a customer service query is split into steps to identify products and categories mentioned in the query.
   - Product information is looked up from a catalog, and relevant details are formatted and provided to the model to generate a final response.
   - Helper functions are used to fetch product details by name or category and format them for the model.

4. **Context Management**:
   - By selectively loading relevant information into the model’s context, the system avoids overwhelming the model with unnecessary details.
   - This is important given the token limitations and costs associated with language models.

5. **Use of External Tools**:
   - The approach allows for the use of external tools, such as looking up information in a product catalog or calling an API, which can’t be achieved with a single prompt.

6. **Benefits of Structured Responses**:
   - Structured responses, like lists of objects, make it easier to manage and process information programmatically.

7. **Text Embeddings for Information Retrieval**:
   - Text embeddings enable efficient knowledge retrieval and allow for fuzzy or semantic search, finding relevant information without exact keywords.


# 6. Check Outputs
**Summary of the Transcript:**

In this video, the focus is on checking the outputs generated by a system to ensure their quality, relevance, and safety before displaying them to users. The process involves using the moderation API for filtering and moderating outputs, similar to its use in evaluating inputs. Here are the key points covered:

1. **Moderation API:**
   - The moderation API can be used to filter outputs to ensure they meet quality and safety standards.
   - An example response was shown where the moderation API flagged outputs based on certain thresholds.
   - Adjusting thresholds for flagging outputs can be crucial for applications targeting sensitive audiences.

2. **Output Evaluation:**
   - Outputs can also be evaluated by asking the model itself if the generated response meets the quality standards and follows a defined rubric.
   - This involves providing the generated output as input to the model and asking it to rate the quality.
   - Examples include using a simple "Y" (Yes) or "N" (No) to indicate if the response sufficiently answers the question and uses the retrieved information correctly.

3. **Advanced Model Use:**
   - Using more advanced models, like GPT-4, is recommended for better reasoning and accuracy in evaluating outputs.
   - The video also mentions the potential use of more complex rubrics or guidelines to evaluate the tone and adherence to brand guidelines.

4. **Practical Considerations:**
   - Evaluating outputs using the model itself can be useful but might not be necessary for most cases, especially with advanced models.
   - This approach can increase latency and cost due to additional model calls and token usage.
   - It is suggested to use this method only if extremely high accuracy is critical for the application.

# 7. Evaluations
