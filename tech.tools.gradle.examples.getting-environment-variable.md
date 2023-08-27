---
id: amc5b653xa142aqh3wkbrud
title: Getting Environment Variable
desc: ''
updated: 1678047410098
created: 1678047410098
---

```kts
task("print-env-variable") {
    doLast {
        val ENV_VAR_NAME = "MY_ENV_VAR"

        val envVarValue: String? = System.getenv(ENV_VAR_NAME)
        if (envVarValue != null) {
            println("The value of $ENV_VAR_NAME is $envVarValue")
        } else {
            println("$ENV_VAR_NAME is not set.")

            throw RuntimeException("$ENV_VAR_NAME environment variable not set")
        }
    }
}
```