---
id: t0j0332mpi7ph3mp6xurvjc
title: CSRF-cross-site-request-forger
desc: ''
updated: 1681436157838
created: 1681436157838
---

Attackers fools an application to allow him to perform sensitive operations, on behalf of legitimate user. That they shouldn't have access to. 

## Example
For example. I visit Amazon.com, login. Amazon gives my browser a cookie to remember me. 

Then I visit badsite.com. Badsite.com uses some javascript to issue a request to Amazon.com from within badsite.com session. And the browser automatically attaches cookies to this request. (Then I visit badsite.com. Badsite.com uses some javascript to issue a request to Amazon.com from within badsite.com session. And the browser automatically attaches cookies to this request.)