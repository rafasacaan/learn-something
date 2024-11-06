# Prompt techniques
Taken from [John Berryman - Parliance Labs](https://parlance-labs.com/education/prompt_eng/berryman.html)

### Technique 1. Few-shot prompting

First, engineers gave a few examples before prompting the actual task. Sometimes, the few shot examples bleed into the answers.

### Technique 2. Chain of thought reasoning

Using few-shot prompting, you provide explitcitly the reasoning that builds and supports each answer in each example. By conditioning the prompt, you force it to talk through the answer in order to get it right.

### Technique 3. Document mimicry

The most important. Imagine that the document type is a transcript. It tells a story t condition a particular response. It uses markdown to establish structure.
Example:

```bash
# IT Support Assistant
The following is a transcript between an award winning IT support rep and a customer.

## Customer:
My cable is out! And i am going to miss the superbowl!

## Support Assistant:
Let´s figure out how to diagnose your problem ...
```

### Promp crafting intuitions
- LLMs understand better when using familiar language and constructs
- LLMs get distracted: be veery concise about the output we need and what to consider. Don´t be ambiguous.
- If information is not in their training, nor in the prompt, then there is no way of obtaining that information
- LLMs are dumb mechanical humans

### Building LLM apps

We can think of this as a problem where we need to transform text into LLM domain and back. 
```bash
User -> user problem -> [app: transform user problem into model domain] -> prompt -> LLM
User <- solution <- [app:transform completion into a solution/update to the problem] <- completion <- LLM
```

The hardest part is **transforming the use problem into model domain**.

### Creating the prompt
- Collect context
- Rank context
- Trim context
- Assembling prompt into something that looks like the training set
  






