# python_docker
能不能有一种稳定的环境，让我可以安心跑python呢

# 官方镜像直接启动

当前路径下创建 test.py 文件

docker 会自动拉取python官方制作的镜像 python:3.11-slim

docker run -v $PWD:/app -w /app python:3.11-slim python test.py
# dockerfile
```
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

CMD ["python"]
```
