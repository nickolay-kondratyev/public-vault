---
id: cwe7xwq796j5css44szpo0n
title: be-careful-with-using-markdown-table-formatting
desc: ''
updated: 1687653795556
created: 1687651803108
---

Consider using markdown table formatting for easier surveying of options.

Look at the following for an example:

<details>
<summary>An example of prompt in regards to Google Guide</summary>

I have a problem. I need to setup a Dependency Injection framework for my app and I want to use Google Guice. Could you brainstorm and present multiple distinct options as a Markdown table of options. Please explain your reasoning for including each option and also give each option an random id. Here's example of formatting of a line that I'd like you to generate:

Header line
```
| RandomId |  Option | Reasoning |
```

An example of {RandomId} is `as3133bn`.

(Render markdown instead of putting into the code block)
</details>


<details>
<summary>Templated Example</summary>

I have a problem. <INSERT_YOUR_PROBLEM_HERE>. Could you brainstorm and present multiple distinct options as a Markdown table of options. Please explain your reasoning for including each option and also give each option an random id. Here's example of formatting of a line that I'd like you to generate:

Header line
```
| RandomId |  Option | Reasoning |
```

An example of {RandomId} is `as3133bn`.

(Render markdown instead of putting into the code block)
</details>

## Concerns: Presents shorter answer

<details>
<summary>Concerns: Presents shorter answers. Longer Answers from LLMs are considered better</summary>


Consider:

![[tech.tools.ChatGPT.th.LLMs-the-longer-the-answer-the-better]]

Well when using a table the answers seem to be much shorter. Hence using the table is a concern.

</details>

