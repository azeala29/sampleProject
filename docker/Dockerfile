FROM jenkins/jenkins:lts
LABEL authors="dujuanfeng"

ENTRYPOINT ["top", "-b"]

# 切换到 root 用户安装依赖
USER root

# 安装 Python 3
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# 复制 requirements 文件
COPY requirements.txt .

# 安装依赖
RUN pip install --no-cache-dir -r requirements.txt


# 切换回 jenkins 用户
USER jenkins

# 重新构建和运行
#docker build -t my-jenkins-python .
#docker run -d -p 8080:8080 -p 50000:50000 -v jenkins_data:/var/jenkins_home my-jenkins-python
