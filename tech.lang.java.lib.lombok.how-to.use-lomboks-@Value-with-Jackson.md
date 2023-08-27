---
id: ru9xuerob0f6m4xkli5bcnt
title: use-lomboks-@Value-with-Jackson
desc: ''
updated: 1668782072432
created: 1668205820056
---

Immutability is very important in maintainable software development. And we don't want to write boiler plate over and over again. Hence:

Here is how to use [[tech.lang.java.lib.lombok.annotations.@Value]] with Jackson: 

```java
import com.fasterxml.jackson.annotation.JsonAutoDetect;
import com.fasterxml.jackson.annotation.PropertyAccessor;
import com.fasterxml.jackson.databind.ObjectMapper;

import lombok.AccessLevel;
import lombok.AllArgsConstructor;
import lombok.NoArgsConstructor;
import lombok.Value;

public class JacksonSandbox {
    public static void main(String[] args) throws Exception {

        final ObjectMapper mapper = new ObjectMapper();
        mapper.setVisibility(PropertyAccessor.FIELD, JsonAutoDetect.Visibility.ANY);
        final Person person = mapper.readValue("{\"name\":\"John\"}", Person.class);

        System.out.println(person);
    }

    @Value
    @NoArgsConstructor(force = true, access = AccessLevel.PRIVATE)
    @AllArgsConstructor
    public static class Person {
        String name;
    }
}
```

Credit: https://stackoverflow.com/a/55957865/7858768


#tech.immutability