##### 【Docker 知识点】

[图灵星球教程](https://turingplanet.org/category/%e5%85%a8%e6%a0%88%e5%bc%80%e5%8f%91/docker%e5%85%a5%e9%97%a8%e6%95%99%e7%a8%8b/)

```bash
// bind mount 使用
$docker run -p 3001:3000 -v local_folder_path:/app/volume_data volumn-app-frontend

// volume 演示
$docker volume create book-data
$docker volume inspect book-data
 => 
 [
 	{
 		"CreateAt":,
 		"Driver":,
 		"Labels":,
 		"Mountpoint":"/var/lib/docker/volumes/book-data/_data",
 		"Name":,
 		"Options":{},
 		"Scope":"local"
 	}
 ]
// Mountpoint 是 docker 帮着创建并管理的路径，自己没法访问
$docker run -p 3001:3000 -v book-data:/app/volume_data volumn-app-frontend
$docker run -v book-data:/book-data -it ubuntu
$/# ls
 => 会显示 book-data 文件夹
 本地volume book-data ~ frontend /app/volume_data ~ ubuntu /book-data 三个对应
$/# echo {\"title\":\"UBook\"} > book.json

// 与 docker-compose.yml 配合使用，管理多个 container
$docker-compose up 
$docker-compose stop // 关 
$docker-compose down 
$docker build . -f Dockerfile -t app


// Redis 相关
$brew services start redis

// registry 的用法
$docker run -d -p 5000:5000 -name registry registry:2 // 在本地开启 Docker Registry
$docker pull ubuntu
$docker tag ubuntu localhost:5000/my-ubuntu
$docker push localhost:5000/my-ubuntu
$docker images
$docker rmi ubuntu localhost:5000/my-ubuntu
$docker images
$docker pull localhost:5000/my-ubuntu // 从本地 registry 抓
$docker run -it localhost:5000/my-ubuntu // 测试
$/# ls
	=> ...目录

// Docker Hub
// 0. 创建用户 accName
// 1. 创建仓库 repoName
$docker tag localhost:5000/my-ubuntu accName/repoName
$docker push accName/repoName
// => 官网可以查看到，，已经上传成功
$docker rmi accName/repoName
$docker images // 检查本地没有 accName/repoName
$docker pull accName/repoName
$docker run -it accName/repoName // => 正常显示 ubuntu 提示符
```

