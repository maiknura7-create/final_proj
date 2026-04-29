# 🧊 Smart Fridge AI: Personalized Recipe & Nutrition Agent

Smart Fridge AI is an intelligent kitchen assistant built using **LangGraph**, **Streamlit**, and **Groq (Llama 3)**. It manages your fridge inventory, generates detailed recipes scaled to your household size, provides comprehensive nutritional analysis based on your personal fitness profile, and tracks leftovers.

## 🚀 Features

- **Inventory Tracking**: Real-time view of your fridge contents with expiration alerts.
- **Dynamic Recipe Generation**: A "Chef Node" creates detailed culinary instructions scaled perfectly for the number of people you are cooking for.
- **Fitness-Aligned Nutrition**: A "Dietician Node" calculates calories, macros, and provides health advice tailored to your weight and activity level.
- **Leftover Management**: Automatically calculates remaining ingredients in your fridge after a recipe is "prepared".
- **Interactive UI**: A clean, professional Streamlit interface with a dual-view system (Fridge View vs. Recipe View).

## 🛠️ Tech Stack

- **Framework**: [LangGraph](https://github.com/langchain-ai/langgraph) (for stateful multi-agent orchestration)
- **LLM**: Groq Llama-3.3-70b-versatile
- **Frontend**: [Streamlit](https://streamlit.io/)
- **Data Handling**: Pydantic (Structured Outputs)
- **Language**: Python 3.9+

## 📁 Project Structure

```text
├── app.py              # Streamlit frontend and UI logic
├── project.py          # LangGraph state machine and agent nodes
├── prompts.py          # System prompts for Chef and Dietician agents
├── fridge.json         # Local database for inventory tracking
└── README.md           # Project documentation
```


## ⚙️ Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/smart-fridge-ai.git
   cd smart-fridge-ai
   ```

2. **Install dependencies:**
   ```bash
   pip install streamlit langchain-groq langgraph pydantic
   ```

3. **Set up your Groq API Key:**
   Update the `os.environ["GROQ_API_KEY"]` in `project.py` or set it as an environment variable:
   ```bash
   export GROQ_API_KEY='your_api_key_here'
   ```

4. **Prepare your inventory:**
   Ensure `fridge.json` is populated with your current stock. Example format:
   ```json
   {
     "inventory": [
       {"item": "chicken", "expiry_days": 2, "mass_g": 500},
       {"item": "tomato", "expiry_days": 1, "mass_g": 300}
     ]
   }
   ```

## 🖥️ Running the App

Start the Streamlit server by running:

```bash
streamlit run app.py
```

## 🧠 How It Works (The Graph)

The application uses a directed acyclic graph (DAG) to process information:

1. **Inventory Node**: Reads `fridge.json` and prepares the data for the LLM.
2. **Chef Node**: Receives the inventory and user profile (people count) to generate a structured `Recipe` object.
3. **Dietician Node**: Analyzes the generated recipe against the user's weight/activity to provide fitness insights.
4. **Leftovers Node**: Uses Regex logic to calculate what remains in the fridge based on the ingredients used by the Chef.

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for new features (like image generation for recipes or database integration).

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
