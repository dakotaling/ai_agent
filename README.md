# AI Agent

A Python-based AI agent that leverages Google's Generative AI to create interactive chatbot functionality with a focus on functional programming principles.

## Overview

This project demonstrates the implementation of an AI-powered agent using Google's Generative AI API. The codebase emphasizes functional programming concepts including pure functions, immutability, higher-order functions, and function composition to create maintainable and predictable code.

## Setup

### Prerequisites
- Python 3.8 or higher
- Git
- A Google AI Studio account and API key

### API Key Setup

1. **Create a Google AI Studio account** (if you don't already have one):
   - Visit [Google AI Studio](https://aistudio.google.com/)
   - Sign in with your Google account

2. **Generate an API key**:
   - In Google AI Studio, click the "Create API Key" button
   - If you have an existing Google Cloud Platform (GCP) project, you can create the API key within that project
   - If you don't have a GCP project, AI Studio will automatically create one for you
   - For detailed instructions, refer to the [Google AI Studio API documentation](https://ai.google.dev/gemini-api/docs/api-key)

3. **Secure your API key**:
   - Copy the generated API key immediately (you may not be able to view it again)
   - Store it securely and never share it publicly

### Installation

1. **Clone the repository and navigate to the project directory:**
   ```bash
   git clone https://github.com/dakotaling/ai_agent.git
   cd ai_agent
   ```

2. **Create a virtual environment:**
   ```bash
   python3 -m venv venv
   ```

3. **Activate the virtual environment:**
   
   On macOS/Linux:
   ```bash
   source venv/bin/activate
   ```
   
   On Windows:
   ```bash
   venv\Scripts\activate
   ```
   
   You should see `(venv)` at the beginning of your terminal prompt.

4. **Install the required dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

5. **Configure your environment variables:**
   - Create a `.env` file in the project root directory
   - Add your Google AI (Gemini) API key:
     ```env
     GEMINI_API_KEY="your_api_key_here"
     ```
   - Ensure the `.env` file is added to your `.gitignore` to prevent committing sensitive information

6. **Verify your setup:**
   - The `main.py` file should load environment variables using the `python-dotenv` library
   - Your API key will be read from the `.env` file when the program starts

7. **Link the config file to the correct directory** (if applicable)

### Running the Agent

To run the chatbot, use:
```bash
python3 main.py "Create a calculator GUI"
```

Replace the quoted text with your desired prompt.

## Functional Programming Concepts

This project demonstrates several key functional programming principles:

### Pure Functions
The project utilizes pure functions that:
- Always return the same output for the same input
- Have no side effects
- Make the code more predictable and easier to test
- Enable better unit testing and debugging

### Immutability
Data structures are treated as immutable where possible:
- Configuration objects are not modified after creation
- State changes create new objects rather than mutating existing ones
- Reduces bugs related to unexpected state changes
- Improves thread safety and concurrent execution

### Higher-Order Functions
Functions that operate on other functions:
- Used for processing AI responses and transforming data
- Implementing callback patterns for asynchronous operations
- Creating reusable function decorators for logging and error handling
- Enabling function composition for complex data transformations

### Function Composition
Breaking down complex operations into smaller, composable functions:
- **Message processing pipelines** - Functions composed to handle user input through validation, processing, and response generation
- **Response transformation chains** - Sequential function calls that refine and format AI responses
- **Error handling and validation flows** - Composed error handling that gracefully manages different failure scenarios
- **Modular function architecture** - The `functions/` directory contains composable modules that can be combined for complex tasks

### Declarative Programming
Focus on what to do rather than how to do it:
- **Configuration-driven behavior** - The `config.py` module defines system behavior declaratively
- **Template-based prompt management** - The `prompts.py` file uses declarative templates for AI interactions
- **Functional data processing pipelines** - Data flows through pure functions without imperative control structures
- **Reduced imperative control flow** - Emphasis on functional composition over procedural programming

## Functional Architecture Benefits

This functional approach provides several advantages:

1. **Testability** - Pure functions in `functions/` and `call_function.py` are easily unit tested
2. **Maintainability** - Clear separation between configuration (`config.py`), logic (`main.py`), and specialized functions
3. **Reusability** - Functions can be composed and reused across different contexts
4. **Predictability** - Immutable data structures and pure functions reduce unexpected behavior
5. **Modularity** - The calculator module demonstrates how functionality can be cleanly separated

## Project Structure

```
ai_agent/
├── calculator/          # Example directory to use LLM with
├── functions/           # Core function definitions and utilities
├── main.py             # Entry point - loads .env and reads API key
├── call_function.py    # Function calling and execution logic
├── config.py           # Configuration management
├── prompts.py          # AI prompt templates and management
├── tests.py            # Unit tests and test cases
├── requirements.txt    # Python dependencies
├── .env                # Environment variables
├── .gitignore         # Git ignore file (includes .env)
└── README.md          # This file
```

## Architecture Overview

The project follows a modular architecture with clear separation of concerns:

- **`main.py`** - Application entry point that loads environment variables and orchestrates the chatbot
- **`config.py`** - Centralized configuration management using functional programming principles
- **`prompts.py`** - Template-based prompt management for consistent AI interactions
- **`call_function.py`** - Function calling logic that enables the AI to execute specific tasks
- **`functions/`** - Directory containing reusable function modules
- **`calculator/`** - Specialized module for calculator functionality
- **`tests.py`** - Comprehensive test suite ensuring code reliability

## Dependencies

The project requires the following Python packages:

- `google-genai==1.12.1` - Google's Generative AI SDK for Gemini API
- `python-dotenv==1.1.0` - Environment variable management from .env files

## Environment Variables

Create a `.env` file in your project root with the following structure:

```env
# Google AI Studio API Key
GEMINI_API_KEY="your_api_key_here"
```

**Important**: Never commit your `.env` file to version control. The `.gitignore` file should include:
```
.env
venv/
__pycache__/
```

## Features

- **Interactive AI-powered chatbot** - Built with Google's Gemini API for natural language understanding
- **Functional programming architecture** - Emphasizes pure functions, immutability, and composition
- **Modular function system** - Extensible function modules in the `functions/` directory
- **Calculator functionality** - Dedicated calculator module for mathematical operations
- **Template-based prompts** - Centralized prompt management in `prompts.py`
- **Configuration management** - Environment-based configuration via `config.py`
- **Function calling capabilities** - AI can execute specific functions through `call_function.py`
- **Comprehensive testing** - Unit tests ensure reliability and maintainability
- **Environment-based configuration** - Secure API key management through `.env` files
- **Extensible design** - Easy to add new functions and capabilities

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes following functional programming principles
4. Add tests for new functionality
5. Commit your changes (`git commit -m 'Add some amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Troubleshooting

### Common Issues

1. **Virtual environment not activated:** Ensure you see `(venv)` in your terminal prompt
2. **Missing or invalid API key:** 
   - Check that your `.env` file contains a valid Gemini API key
   - Verify the API key format: `GEMINI_API_KEY="your_key_here"`
   - Ensure the API key has proper permissions in Google AI Studio
3. **Import errors:** Verify all dependencies are installed with `pip install -r requirements.txt`
4. **Environment variables not loading:** Ensure `python-dotenv` is installed and `main.py` properly loads the `.env` file

### Getting Help

- Check the issues page for known problems
- Review the [Google AI Studio documentation](https://ai.google.dev/gemini-api/docs) for API-related questions
- Consult the [Google AI Python SDK documentation](https://ai.google.dev/gemini-api/docs/python-quickstart) for implementation details
- Ensure your Python version is 3.8 or higher

## Useful Resources

- [Google AI Studio](https://aistudio.google.com/) - Create and manage API keys
- [Gemini API Documentation](https://ai.google.dev/gemini-api/docs) - Complete API reference
- [Google AI Python Quickstart](https://ai.google.dev/gemini-api/docs/python-quickstart) - Getting started guide
- [Python dotenv Documentation](https://pypi.org/project/python-dotenv/) - Environment variable management

## Acknowledgments

- Google for providing the Generative AI API
- The Python community for excellent functional programming libraries
- Contributors and maintainers of this project
