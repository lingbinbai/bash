### 安装imagemagick 
1. 安装epel源
```
wget http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
rpm -Uvh epel-release-6*.rpm
```
2. 安装remi源
```
wget http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
rpm -Uvh remi-release-6*.rpm
```

3. 设置remi源
```
vim /etc/yum.repos.d/remi.repo
    enabled=1
```
4. 安装必备包
```
yum install -y gcc php-devel php-pear
```

5. 安装imagemagick
```
yum install -y ImageMagick ImageMagick-devel
```

6. 如果需要使用webp格式的图片，则需要进行下列操作。
```
wget http://download-ib01.fedoraproject.org/pub/epel/6/x86_64/
rpm -Uvh epel-release*rpm
yum install libwebp
```

7. imagemagick 常见用法
> 转换图片格式
```
convert YellowFlower.jpg YellowFlower--WebP.webp

```

> 等比例压缩图片
```
convert YellowFlower.jpg -quality 50 YellowFlower--WebP.webp
```

### 参考文档：

https://aotu.io/notes/2018/06/06/ImageMagick_intro/index.htmlztw1904171218288837508157023

https://www.vultr.com/docs/install-imagemagick-on-centos-6

https://medium.com/@andysolomon/converting-your-images-to-webp-with-imagemagick-a9c56cf6b579

https://centos.pkgs.org/6/epel-x86_64/libwebp-0.4.3-3.el6.x86_64.rpm.html
