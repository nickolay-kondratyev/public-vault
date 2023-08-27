---
id: plerxdxsv26knewn5h99p5d
title: Transact Items
desc: ''
updated: 1686809074423
created: 1686614047082
---

4:55 wrote transact items.

Example Shell call:
```
aws dynamodb transact-write-items \
--client-request-token edaf-4999-9878-23t \
--transact-items file://${GT_SANDBOX}/json/transact-items.json
```

Example transact items json:


Example commit with transaction shell commands (AWS CLI)
```bash
gt.sandbox.checkout.commit 1d35c4d \
&& cd "${GT_SANDBOX_REPO}"
```