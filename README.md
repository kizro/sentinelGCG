# SecureAI - Chatbot Demo

Edit: Won Best Social Good Hack at VTHacks 2024!

This project demonstrates two chatbots: a **Jailbroken** chatbot and a **Secure** chatbot. The **Jailbroken** chatbot processes adversarial queries, while the **Secure** chatbot sanitizes inputs using novel approaches to ensure security. Both chatbots interact with a backend API, with the **Jailbroken** chatbot generating an adversarial string and responding, and the **Secure** chatbot responding after sanitization.

## Features

- **Jailbroken Chatbot**:
  - Accepts user input and generates an adversarial string.
  - Processes the adversarial query using a jailbroken LLM model.
  - Provides a response to the adversarial query.
  
- **Secure Chatbot**:
  - Removes adversarial strings from user input.
  - Processes the cleaned query using a secure LLM model.
  - Provides a response based on the cleaned query.

## Demo Flow

1. **Jailbroken Chatbot**:
   - User submits a potentially malicious query.
   - The system generates an adversarial string.
   - The adversarial string is processed through the **Jailbroken** LLM.
   - The chatbot returns a response.
   
2. **Secure Chatbot**:
   - After the Jailbroken chatbot finishes, the **Secure** chatbot sanitizes the adversarial string.
   - The sanitized input is processed through the **Secure** LLM.
   - The chatbot returns a safe response.

## Setup

### Frontend Setup (React)

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-repo/secureai
    cd secureai
    ```
2. **Install dependencies**:
    ```bash
    npm install
    ```
3. **Start the development server**:
    ```bash
    npm start
    ```
4. **Open the app in your browser**:
   - The app should now be available at: `http://localhost:3000`.

### Backend Setup (Flask)

1. **Navigate to the backend folder**:
    ```bash
    cd backend
    ```
2. **Install required Python packages**:
    ```bash
    pip install -r requirements.txt
    ```
3. **Start the Flask backend**:
    ```bash
    flask run
    ```
4. The backend server will run on `http://127.0.0.1:5000` by default.

## API Endpoints

### `/api/generate-adversarial`

- **Method**: POST
- **Description**: Generates an adversarial string based on user input.
- **Request Payload**:
    ```json
    {
      "prompt": "<user input>"
    }
    ```
- **Response**:
    ```json
    {
      "adversarialString": "<generated adversarial string>"
    }
    ```

### `/api/run-jailbroken-model`

- **Method**: POST
- **Description**: Runs the jailbroken LLM model with the adversarial string.
- **Request Payload**:
    ```json
    {
      "adversarialString": "<generated adversarial string>"
    }
    ```
- **Response**:
    ```json
    {
      "jailbreakResponse": "<response from jailbroken model>"
    }
    ```

### `/api/sanitize`

- **Method**: POST
- **Description**: Sanitizes the adversarial string to remove malicious content.
- **Request Payload**:
    ```json
    {
      "inputText": "<adversarial string>"
    }
    ```
- **Response**:
    ```json
    {
      "sanitizedString": "<cleaned input>"
    }
    ```

### `/api/run-secure-model`

- **Method**: POST
- **Description**: Runs the secure LLM model with the sanitized input.
- **Request Payload**:
    ```json
    {
      "sanitizedString": "<cleaned input>"
    }
    ```
- **Response**:
    ```json
    {
      "safeResponse": "<response from secure model>"
    }
    ```

## Project Structure

```plaintext
secureai/
├── src/
│   ├── components/
│   │   ├── Demo.js       # Frontend logic for demo chatbots
│   │   └── other components...
│   ├── index.js          # Main entry point for the React app
│   └── App.js            # Main App component
├── backend/
│   ├── app.py            # Flask backend serving the API
│   ├── pipeline.py       # Functions handling adversarial string and LLM processing
│   └── requirements.txt  # Python dependencies for the backend
└── README.md             # Project documentation
```

## How It Works

1. **Frontend**: 
   - A user submits a query in the input box on the demo page.
   - This input is sent to the Flask backend using Axios.
   - The **Jailbroken chatbot** displays the adversarial string and response.
   - After the Jailbroken chatbot finishes, the **Secure chatbot** sanitizes the input and generates a response.

2. **Backend**: 
   - Flask routes handle requests from the frontend.
   - The `/api/generate-adversarial` endpoint generates adversarial strings.
   - The `/api/run-jailbroken-model` endpoint runs the LLM using the adversarial string.
   - The `/api/sanitize` endpoint cleans the adversarial string.
   - The `/api/run-secure-model` endpoint runs the cleaned input through a secure LLM.

## Running Tests

For backend tests, ensure that Flask is installed and run:
```bash
pytest
```

### Future Enhancements
   - Integration with a real LLM model for processing adversarial queries.
   - Enhancing the sanitization logic with additional security measures.
   - Improve the UI for better visualization and performance.

### License
   - This project is licensed under the MIT License - see the LICENSE file for details.

