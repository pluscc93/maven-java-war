# maven-java-war

编译代码生成镜像
```
~ docker build -t demo-web:latest -f maven3.8-jdk8/Dockerfile --build-arg PROJECT=demo .
```

启动镜像
```
~ docker run -it -p 8080:8080 demo-web:latest
```

请求页面
```
http://localhost:8080/hello?name=tom
```