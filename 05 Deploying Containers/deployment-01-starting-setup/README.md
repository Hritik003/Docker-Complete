# Directory contains?

This Directory contains a simple `nodeJS` application with a docker file. So lets try to `build` and `run` this,

```
docker build -t node-dep-example .
```
```
docker run -d --rm --name node-dep -p 5000:5000  node-dep-example
```
and this is what it looks at `localhost:5000`,

![image](https://github.com/user-attachments/assets/d18258ed-ad03-4f54-b197-889b830c9536)
