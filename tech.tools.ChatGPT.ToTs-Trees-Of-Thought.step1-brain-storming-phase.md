---
id: aabekjsemp664w5blwa0rz8
title: "ToTs Step1: Brain Storming Phase"
desc: ''
updated: 1687663940741
created: 1687648146092
---

Purpose: **Generate diverse range of solutions to a problem.**

Get the LLM to put out high level ideas. 

Get LLM to provide reasoning, preferably stating the factors to consider. 

> The first phase of the Tree of Thought process involves brainstorming diverse potential solutions to a given problem. In this stage, you can ask your AI model to generate three or more options while considering various factors. [allabtai.com](https://www.allabtai.com/chatgpt-tree-of-thoughts-prompt-engineering/)

<details>
<summary>Example from All About AI</summary>
> Prompt: I have a problem related to [describe your problem area]. Could you brainstorm three distinct solutions? Please consider a variety of factors such as [Your perfect factors] - [ref](https://www.allabtai.com/the-tree-of-thoughts-prompt-template/)
</details>


<details>
<summary>Templated Example without Markdown</summary>

You are: <INSERT_PREPPING_ROLE_DESCRIPTION_HERE>

I have the following problem

My_Problem=<INSERT_YOUR_PROBLEM_HERE>. 

My_Background_In_Relation_To_This_Problem=<INSERT_YOUR_BACKGROUND_HERE_OR_DELETE_THIS_LINE>

Could you brainstorm and present multiple distinct solutions? Please explain your reasoning for including each option. Please consider a variety of factors including but not limited to: [<INSERT_YOUR_FACTORS_HERE>]

Also give each option a sequenced number and a random id, so that we can reference this id later. An example of {RandomId} is `as3133bn`.
</details>


## Navigation
Next step: [[tech.tools.ChatGPT.ToTs-Trees-Of-Thought.step2-evaluation-phase]]