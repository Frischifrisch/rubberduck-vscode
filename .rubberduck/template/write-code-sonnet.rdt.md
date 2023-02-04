```json conversation-template
{
  "id": "explain-code-with-sonnet",
  "engineVersion": 0,
  "type": "selected-code-analysis-chat",
  "label": "Write a code sonnet",
  "description": "Describe the selected code, Shakespeare style.",
  "icon": {
    "type": "codicon",
    "value": "feedback"
  },
  "isEnabled": false,
  "initVariableRequirements": [
    {
      "type": "non-empty-text",
      "variable": "selectedText"
    }
  ],
  "analysisPlaceholder": "Composing poetry",
  "analysisPrompt": {
    "template": {
      "type": "sections",
      "sections": [
        {
          "type": "lines",
          "title": "Instructions",
          "lines": [
            "Describe the code below in the style of a Shakespeare sonnet."
          ]
        },
        {
          "type": "optional-selected-code",
          "title": "Selected Code"
        },
        {
          "type": "lines",
          "title": "Task",
          "lines": ["Describe the code in the style of a Shakespeare sonnet."]
        },
        {
          "type": "lines",
          "title": "Sonnet",
          "lines": []
        }
      ]
    },
    "maxTokens": 1024,
    "temperature": 0.5
  },
  "chatTitle": "Code Sonnet",
  "chatPrompt": {
    "template": {
      "type": "sections",
      "sections": [
        {
          "type": "lines",
          "title": "Instructions",
          "lines": ["Continue the conversation.", "Use 16th century English."]
        },
        {
          "type": "lines",
          "title": "Current Request",
          "lines": ["Developer: ${lastMessage}"]
        },
        {
          "type": "optional-selected-code",
          "title": "Selected Code"
        },
        {
          "type": "lines",
          "title": "Code Summary",
          "lines": ["${firstMessage}"]
        },
        {
          "type": "conversation",
          "excludeFirstMessage": true,
          "roles": {
            "bot": "Shakespeare",
            "user": "Developer"
          }
        },
        {
          "type": "lines",
          "title": "Task",
          "lines": [
            "Write a response that continues the conversation.",
            "Use 16th century English.",
            "Reference events from the 16th century when possible.",
            "Try making it a sonnet."
          ]
        },
        {
          "type": "lines",
          "title": "Response",
          "lines": ["Shakespeare:"]
        }
      ]
    },
    "maxTokens": 1024,
    "stop": ["Shakespeare:", "Developer:"],
    "temperature": 0.5
  }
}
```