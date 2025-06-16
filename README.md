from transformers import pipeline

# Load the LLM
chatbot = pipeline("text-generation", model="distilgpt2")

# Start chat loop
while True:
    user_input = input("You: ")
    if user_input.lower() in ['exit', 'quit']:
        print("Chatbot: Bye!")
        break

    response = chatbot(user_input, max_length=100, num_return_sequences=1)
    print("Chatbot:", response[0]['generated_text'][len(user_input):])
