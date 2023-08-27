---
id: f5knqlh2yv0ndxm46pl7bu0
title: XSS-cross-site-scripting
desc: ''
updated: 1681434441850
created: 1681434441850
---

aka HTML injection.

Attacker injects client-side scripts into a trusted website. 

Breeding ground: whenever a web application accepts user input, and then displays user input within an output field it can be potentially vulnerable to XSS attack.

Examples on a website:
- Comment section.
- Reviews section. 

A script could be injected that will send the cookies, session tokens of another customer to some other website. 

XSS attack injects javascript hence besides sending sensitive information to attacker, it can also rewrite the site. 

## Best Practices
- Understand all your inputs.
- Validate the input on the server side.
- Convert data to a strong type.
- Use allow list approach. Only allowing data that strictly honors your contract and semantics.
- Use context sensitive output encoding. Example
  - HTML output must use HTML encoding
  - XML output must use XML encoding. 

Output encoding, escapes special characters rendering the scripts as plain text, rather than executable script. 