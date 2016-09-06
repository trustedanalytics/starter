---
layout: blog
category: blog
published: false
title: Tips and tricks for Java
---
> [Wiki Home](Home) ▸ **Tips and Tricks for Java**

### Reading application properties with Spring
You can read complex _env_ variables with Spring very easily. For example:

```
"VCAP_APPLICATION": {
    "uris": [
        "sample.url1.com",
        "sample.url2.com"
    ]
}
```
Retrieve the first URI from the _uris_ array. In the _application.yml_ file, type:
```
app:
   url: ${vcap.application.uris[0]:default}
```

Your _code-config_ file should look like this:
```
@Configuration
public class Config {
    @Value("${app.url}")
    private String myAppUrl;
}
```
"sample.url1.com" will be inserted into the _myAppUrl_ variable in Config class.

### Enabling Java gc logs for CF application

cf set-env app-name JAVA_OPTS "-verbose:gc -XX:+PrintGCDetails"

cf restage app-name

### Specifying heap and metaspace size for CF application

Use the newest version of Java buildpack (support for specifying heap size was added in 3.2):
```
cf push <APP-NAME> -p <ARTIFACT> -b https://github.com/cloudfoundry/java-buildpack.git
```
Set environment variables:
```
cf set-env <APP-NAME> JBP_CONFIG_OPEN_JDK_JRE: [memory_calculator: {memory_sizes: { heap: 64M, metaspace: 34M }}]
```
Restage application.


Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.
