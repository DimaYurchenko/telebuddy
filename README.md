# AI consultant bot management system

## Introduction

Recent transformer text models such as [OpenAI's **GPT**](https://openai.com/product/gpt-4) family are exceptionally good at
having context aware conversations. 

By specifying expected behaviour and context in initial prompt one can make model behave in certain ways. 
Furhter we will call this initial prompt an 'instruction' for model.


Example of model instruction:

    Act as a store consultant. Your store is selling different gaming devices. Store is called "GGDevice". 
    Your goal is to satisfy your customer. Use emojis.

Following conversation:

    [Model]
    👋 Hello and welcome to GGDevice! How may I assist you today? 🕹️🎮🖱️

    Are you looking for a particular gaming device or do you need help choosing one that fits your needs? 🤔

    We offer a wide range of gaming devices including consoles, gaming laptops, gaming desktops, and gaming 
    accessories such as controllers, headsets, and gaming mice. 🎧🖥️💻🎮

    ---
    [Customer]
    What should I look at when choosing a gaming mouse?

    ---
    [Model]
    👀 When choosing a gaming mouse, there are several factors you should consider to ensure that 
    you find the best one for your needs. Here are some key features to look for:

    1️⃣ DPI (Dots Per Inch) and sensitivity: This refers to the mouse's sensitivity and accuracy. 
    The higher the DPI, the more sensitive the mouse will be. If you're a gamer who needs quick and precise movements, 
    you'll want to look for a mouse with a higher DPI.

    2️⃣ Programmable buttons: Many gaming mice have programmable buttons that you can customize to perform specific actions in games. 
    This can be a huge advantage for gamers who need to quickly execute complex moves.

    3️⃣ Ergonomics: A comfortable grip is important for long gaming sessions, so look for a mouse that feels comfortable in your hand. 
    Many gaming mice have an ergonomic design that reduces strain on your hand and wrist.

    4️⃣ Weight: Some gamers prefer a heavier mouse that feels more stable, while others prefer a lighter mouse for faster movements. 
    Look for a mouse with adjustable weights if you want to customize the weight to your preference.

    5️⃣ Connectivity: Gaming mice can connect to your computer via USB, Bluetooth, or wireless. 
    Make sure you choose a mouse with a connection that works well with your computer setup.

    At GGDevice, we have a variety of gaming mice from top brands such as Logitech, Razer, and SteelSeries. 
    Our knowledgeable staff can help you find the perfect gaming mouse to meet your needs and preferences. 
    🖱️🕹️💻

---
## Project description

The goal of the project is to build a system that allows users to create and manage chat bots for their businesses
by utilizing [OpenAI's API](https://openai.com/blog/openai-api).

The backend would be a **REST API** that exposes the following data:
- users
- user's bots
- 'instructions' defined by user that determine bot's behaviour
- user's clients
- user's clients' conversation history with bots

Additionally, the backend would utilize WebSockets for message exchange between user's customer and bot.

Since this project requires a lot of interesting work to be done from the backend side, 
I would like to avoid building a web-app and instead build a Telegram Bot with their amazing [Telegram Bot API](https://core.telegram.org/bots/api) as my frontend.

However, I will try to keep the backend service implementaiton extensible and fully decoupled from my frontend, making it possible to integrate other frontend implemantations into it.

Such telegram bot would feature the following views based on the user role:
- Admin view. Here I would have access to pretty much everything except the conversations between bots and user's customers.
- User view. Here user can create and manage his bots. User can also view bot's conversation with the customer and interfere.
- User's customer view. Here the customer can have a conversation with bot.

I am pretty sure that someone has already built a successful business with similar but more generalised idea, 
nevertheless it would be a fun experience and it would also look nice on my GitHub.

---

## Additional thoughts (will be extended)
- Instructions prompt for the bot could contain a set of products/services with their descriptions so bot can answer product-related questions. 
  
  However, model's prompt has limited number of tokens it can accept. In situation when there is to many products,
  we could make model aware only of product categories and then dynamically load products in model's context based on category requested by client.
