# ctfd
ctfd动态靶机修改版支持一键部署，多处优化，中文界面优化，去除无用界面
以centos为例：部署方法可以查看我的博客
https://blog.csdn.net/zwy3327078581/article/details/134516634?spm=1001.2014.3001.5501

1.yum update

2.yum install -y yum-utils

3.yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

4.yum list docker-ce --showduplicates | sort -r

5.yum install -y docker-ce-24.0.7 docker-ce-cli-24.0.7 containerd.io

下载docker-compose https://github.com/docker/compose/releases/download/1.29.2/docker-compose-Linux-x86_64
下载完后将软件上传至 Linux的【/usr/local/bin】目录下)
6.sudo chmod +x /usr/local/bin/docker-compose

7.sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

8.sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://ehp6t89w.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker

9.git clone -b frp https://github.com/juwenyi/ctfd.git

10.cd CTFd

11.sed -i 's/github.com/gitee.com/g' .gitmodules

12.git submodule update --init

13.docker swarm init

14.docker node ls

15.docker node update --label-add name=linux-1 <nodes><>里面内容替换为节点为上一步步骤中的节点编号例如:olfdml8og5feyjc23ec02gp21

16.docker-compose build

17.docker-compose up -d

根据csdn博主博主Vicosna修改版再度修改。删减内容。
