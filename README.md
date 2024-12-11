# LLMIntentIdentifier

LLMIntentIdentifier is a Large Language Model (LLM)-based intent recognition module designed to enable users to intuitively request database tuning operations in natural language. The system performs two key tasks:

1. **Automatic Classification**: Determines whether the user's input is a request for SQL query generation or knob tuning.
2. **Database Tuning Execution**: If the input is classified as a knob tuning request, the system performs the appropriate tuning operations to enhance database performance.

The module processes natural language inputs to identify the intent and generate the corresponding SQL query or knob tuning action to be applied to the database. It consists of three main stages:

### 1. Input Generation
In this stage, the system generates structured input for the LLM, which includes:
- **Few-shot examples**: Pairs of requests and corresponding intents to provide context for intent identification.
- **User request**: The new natural language input from the user.
- **Task instructions**: Explanations for the intent recognition task.

The few-shot examples help the model leverage its parametric knowledge from pretraining to infer the user's intent accurately.

### 2. LLM-based Inference
The structured input is passed to the LLM, which generates an intent classification result in the form of an `f_tune()` function. The output specifies:
- `"true"` if the request is identified as a knob tuning task.
- `"false"` if the request is identified as SQL query generation.

### 3. Post-processing
The output of the `f_tune()` function is validated and processed using regular expressions to return a final intent classification as `"true"` or `"false"`. This ensures accurate understanding of the user's intent and facilitates the appropriate subsequent action.

By automating the classification of database tuning and query translation tasks, LLMIntentIdentifier significantly improves user experience and operational efficiency.

