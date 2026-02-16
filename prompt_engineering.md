## Prompt Engineering Best Practices
# Prompt Engineering Best Practices

- Write clear, specific instructions with context.
- Use delimiters to separate input from instructions.
- Provide examples (few-shot) for complex tasks.
- Specify the desired output format (JSON, markdown, etc).
- Use chain-of-thought reasoning for multi-step problems.
- Iterate on prompts systematically, testing edge cases.

## Python Example

from openai import OpenAI

client = OpenAI()

system_prompt = """You are a helpful assistant that extracts structured data.
Always respond in valid JSON format."""

user_prompt = """Extract the name, role, and company from the following text.

Text: "Jane Smith is a Senior ML Engineer at Anthropic."

Output format:
{"name": "...", "role": "...", "company": "..."}"""

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": user_prompt}
    ],
    temperature=0
)

print(response.choices[0].message.content)
