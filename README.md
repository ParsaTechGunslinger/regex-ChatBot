# regex-ChatBot

This project is a simple rule-based chatbot built using Python and the NLTK (Natural Language Toolkit) library. The chatbot can respond to various user inputs and gracefully terminate when the user types specific exit commands.

## Features

- **Predefined Pattern-Based Responses**:
  - The chatbot uses a list of predefined patterns to generate responses based on user input.
- **Multiple Exit Commands**:
  - Users can end the conversation by typing `quit`, `finish`, or `stop`.
- **Easy Customization**:
  - The pattern-response pairs can be easily modified or extended to create more complex interactions.

## Requirements

- Python 3.x
- NLTK (Natural Language Toolkit)

## Installation

1. **Install Python**:
   - Make sure Python 3.x is installed. You can download it from [python.org](https://www.python.org/downloads/).

2. **Install the Required Libraries**:
   - You need to install the NLTK library. Open a terminal or command prompt and run:
     ```bash
     pip install nltk
     ```

## Usage

To use the chatbot, follow these steps:

1. **Save the Code**:
   - Create a file named `chatbot.py` and paste the following code into it:

   ```python
   import re
   from nltk.chat.util import Chat, reflections

   # Pairs is a list of patterns and responses.
   pairs = [
       [
           r"(.*)my name is (.*)",
           ["Hello %2, How are you today ?",]
       ],
       [
           r"(.*)help(.*)",
           ["I can help you.",]
       ],
       [
           r"(.*) your name ?",
           ["My name is thecleverprogrammer, but you can just call me robot and I'm a chatbot.",]
       ],
       [
           r"how are you (.*) ?",
           ["I'm doing very well", "I am great!"]
       ],
       [
           r"sorry (.*)",
           ["It's alright", "It's OK, never mind that.",]
       ],
       [
           r"i'm (.*) (good|well|okay|ok)",
           ["Nice to hear that", "Alright, great!"]
       ],
       [
           r"(hi|hey|hello|hola|holla)(.*)",
           ["Hello", "Hey there",]
       ],
       [
           r"what (.*) want ?",
           ["Make me an offer I can't refuse.",]
       ],
       [
           r"(.*)created(.*)",
           ["Aman Kharwal created me using Python's NLTK library.", "Top secret ;)",]
       ],
       [
           r"(.*) (location|city) ?",
           ['New Delhi, India.',]
       ],
       [
           r"(.*)raining in (.*)",
           ["No rain in the past 4 days here in %2", "In %2 there is a 50% chance of rain.",]
       ],
       [
           r"how (.*) health (.*)",
           ["Health is very important, but I am a computer, so I don't need to worry about my health.",]
       ],
       [
           r"(.*)(sports|game|sport)(.*)",
           ["I'm a very big fan of Cricket.",]
       ],
       [
           r"who (.*) (Cricketer|Batsman)?",
           ["Virat Kohli",]
       ],
       [
           r"quit",
           ["Bye for now. See you soon :)", "It was nice talking to you. See you soon :)"]
       ],
       [
           r"(.*)",
           ['That is nice to hear.']
       ],
   ]

   print("Hi, I'm thecleverprogrammer and I like to chat.\nPlease type lowercase English language to start a conversation. Type 'quit' to leave.")

   # Create Chat Bot
   chat = Chat(pairs, reflections)

   # Start conversation
   while True:
       user_input = input("> ")

       # Check if the user wants to quit
       if re.search(r'\b(quit|finish|stop)\b', user_input, re.IGNORECASE):
           print("It was nice talking to you. Goodbye!")
           exit()  # Terminate the program

       # Get the response from the chatbot
       response = chat.respond(user_input)
       print(response)
   
## Example:
  Hi, I'm thecleverprogrammer and I like to chat.
  Please type lowercase English language to start a conversation. Type 'quit' to leave.

  > hello
  Hello

  > my name is John
  Hello John, How are you today?

  > how are you?
  I'm doing very well

  > quit
  It was nice talking to you. Goodbye!

