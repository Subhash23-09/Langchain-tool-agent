# Langchain-tool-agent
<img width="376" height="407" alt="image" src="https://github.com/user-attachments/assets/65cc4dac-4bfe-4e22-a9da-4c5a3ad4190a" />

### Architecture Description

This project implements a **LangChain agent integrated with Gradio** to handle user queries and automatically decide which tool to use for calculations. The architecture is:

1. **User Input (Gradio)**: User enters a query in the Gradio text box.
2. **chat_gradio() function**: Receives the input, decides routing.

   * If the user asks "Which tool was used?", it returns the last tool used.
   * Otherwise, the query is sent to the LangChain agent.
3. **LangChain Agent**:

   * Decides whether to call a tool (`add_numbers` / `multiply_numbers`) or use the LLM (Gemini 2.5 Flash) directly.
   * Updates the conversational memory (`ConversationBufferWindowMemory`) for context.
4. **Memory**: Stores conversation history for multi-turn interactions.
5. **Output to Gradio**: Displays the response in the chat interface.


---

### Libraries Used

| Library                  | Purpose                                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------------------- |
| `langchain_google_genai` | Provides the Gemini LLM wrapper (`ChatGoogleGenerativeAI`) for generating AI responses.                    |
| `langchain.agents`       | Implements `Tool`, `initialize_agent`, and `AgentType` for automatic tool routing and agent orchestration. |
| `langchain.memory`       | Provides `ConversationBufferWindowMemory` to maintain conversation context for multi-turn chats.           |
| `gradio`                 | Creates a web-based interface for user interaction (text input/output).                                    |
| `re`                     | Extracts numbers from user input using regular expressions.                                                |
| `os`                     | Handles environment variables (e.g., storing the Google API key).                                          |

---

<img width="1917" height="812" alt="image" src="https://github.com/user-attachments/assets/1d0f74f3-3048-4a3a-a1a8-21ad81fd92bf" />
