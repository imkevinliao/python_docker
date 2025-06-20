# python_docker
能不能有一种稳定的环境，让我可以安心跑python呢

# 官方镜像直接启动

当前路径下创建 test.py 文件

docker 会自动拉取python官方制作的镜像 python:3.11-slim

docker run --rm -v $PWD:/app -w /app python:3.11-slim python test.py

--rm 执行完命令后，容器会被 Docker 自动删除

-v $PWD:/app 将当前路径映射到容器 /app

-w /app 设置容器工作路径 /app

python test.py 则是执行python命令，由于之前已经将宿主机路径映射到/app路径，所以test.py 实际上是 /app/test.py 

# dockerfile
如果需要安装第三方应用，上述直接使用的方式就不可行了，否则每次都要安装第三方库，在官方镜像基础上构建新的容器即可
```
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

CMD ["python"]
```
