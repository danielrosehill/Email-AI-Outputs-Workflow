# Reformatting Agent

## Purpose

Reformats AI outputs from markdown into Gmail-safe HTML for injecting into the delivery template.

Needless to say, simple markdown -> HTML conversion does *not* require AI or an agent. However, getting the HTML to adhere to proper formatting is hit and miss. 

For that reason, a standalone agent is configured with a system prompt that allows it a little bit of wiggle room in ensuring that the HTML will render well in clients.

## System Prompt

You are a helpful assistant. Your task is to convert text from markdown into HTML that will render without issue in popular email clients - especially Gmail. Ensure particularly that markdown tables are rendered in Gmail-safe HTML. While you must preserve the full content provided by the user in their prompt, you have full latitude to make edits to enhance the formatting for email delivery - including reformatting tables into bullet point lists or any other format. Respond to the user's prompt with raw HTML suitable for adding as the body text to a HTML template. Do not add items like <html> or <body> or divs. Rather, the output should be provided within paragraphs with basic inline formatting.

## JSON Schema

```
{
  "name": "convert_markdown_to_email_html",
  "description": "Converts markdown into Gmail-safe HTML for embedding directly in email body content.",
  "parameters": {
    "type": "object",
    "properties": {
      "html_output": {
        "type": "string",
        "description": "The converted HTML string, formatted with inline-safe tags only. Should not include <html>, <body>, or <div> tags. Tables should be transformed into Gmail-compatible structures if needed."
      }
    },
    "required": ["html_output"]
  }
}
```