# Cover Letter Generator

This project leverages TextBlaze and OpenAI's GPT-3.5 to automatically generate personalized cover letters based on job descriptions. Simply copy a job posting to your clipboard, run the command, and receive a professionally crafted cover letter template that you can customize further.

## How It Works

1. Copy a job description to your clipboard
2. Run the TextBlaze command `/makeCV`
3. Wait a moment while the AI processes your request
4. Receive a tailored cover letter based on the job posting

## Setup Instructions

### Prerequisites

- A TextBlaze account (free or premium)
- An OpenAI API key

### Installation

1. Install the [TextBlaze Chrome extension](https://chrome.google.com/webstore/detail/text-blaze/idgadaccgipmpannjkmfddolnnhmeklj)
2. Create a new TextBlaze snippet called "makeCV"
3. Copy the code below into your snippet
4. Replace the placeholder API key with your actual OpenAI API key
5. Save the snippet

## TextBlaze Code

```
{request_body=tojson(["temperature": 0.3, "max_tokens": 256, "model": "gpt-3.5-turbo", "messages": [["role": "user", "content": "You are a resume expert. Please write a cover letter template for this job posting: {clipboard}"]]], "{model: string, messages: { role: string, content: string }[], temperature: number, max_tokens: number}")}
{=request_body}
{urlload: https://api.openai.com/v1/chat/completions; method=POST; headers=Content-Type:application/json, Authorization:Bearer YOUR_OPENAI_API_KEY_HERE; body={=request_body}; done=(res) -> catch(["result": res, "isloading": no, "haserror" : no], ["name": res, "isloading": no, "haserror": yes]); start=() -> ["isloading": yes]}
{if: isloading}Loading...{else}{response=fromjson(result)["choices"][0]["message"]["content"]}{=response}{endif}
```

> ⚠️ **Important**: Replace `YOUR_OPENAI_API_KEY_HERE` with your actual OpenAI API key. Never share your API key publicly.

## Customization

After generating the cover letter, you should:

1. Replace placeholder text with your actual information
2. Add specific accomplishments relevant to the job requirements
3. Adjust the tone to match the company culture
4. Proofread carefully before sending

## Example

### Sample Job Description

```
Software Engineer - Frontend
XYZ Tech Solutions

About the Role:
We are seeking a talented Frontend Software Engineer to join our growing team. The ideal candidate will have strong experience with React, JavaScript, and modern frontend frameworks.

Responsibilities:
- Develop and maintain responsive web applications
- Collaborate with designers and backend engineers
- Write clean, maintainable code
- Optimize applications for maximum speed and scalability

Requirements:
- 3+ years of experience with JavaScript and React
- Experience with state management libraries (Redux, Context API)
- Knowledge of modern frontend build tools (Webpack, Babel)
- Familiarity with RESTful APIs
- Strong problem-solving skills and attention to detail
```

### Generated Cover Letter

```
[Your Name]
[Your Address]
[City, State ZIP]
[Your Email]
[Your Phone]

[Date]

[Hiring Manager's Name]
[Company Name]
[Company Address]
[City, State ZIP]

Dear [Hiring Manager's Name],

I am writing to express my interest in the Frontend Software Engineer position at XYZ Tech Solutions. With over [X] years of experience developing responsive web applications using React, JavaScript, and modern frontend frameworks, I am confident in my ability to make significant contributions to your team.

Throughout my career, I have focused on writing clean, maintainable code while optimizing applications for maximum speed and scalability. My experience includes:

- Developing and maintaining complex React applications with a focus on performance and user experience
- Implementing state management solutions using Redux and Context API
- Building and configuring frontend build pipelines using Webpack and Babel
- Collaborating closely with designers and backend engineers to create cohesive user experiences
- Working with RESTful APIs to create dynamic and interactive web applications

I am particularly drawn to XYZ Tech Solutions because of [research something about the company and mention it here]. I am excited about the opportunity to bring my problem-solving skills and attention to detail to your team.

Thank you for considering my application. I look forward to the possibility of discussing how my experience aligns with your needs for this role.

Sincerely,

[Your Name]
```

## Security Notes

- Never commit your OpenAI API key to GitHub
- Consider using environment variables or a secrets manager for production use
- Be mindful of any personal information you include in cover letters

## License

This project is licensed under the MIT License - see the LICENSE file for details.
