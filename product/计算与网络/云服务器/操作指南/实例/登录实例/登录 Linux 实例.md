在购买并启动了 Linux 类型的实例后，您可以连接并登录它。根据您本地的操作系统和 CVM 实例是否可被 Internet 访问，不同情况下可以使用不同的登录方式。

## 前提条件
### 使用密码登录的前提条件
**使用密码登录需要使用管理员帐号和对应的密码。**
- 管理员账号：对于不同类型的 Linux 实例，管理员帐号不同，如下表。

| 实例操作系统             | 管理员帐号  |
| ------------------ | ------ |
| SUSE/CentOS/Debian | root   |
| Ubuntu             | ubuntu |

- 密码：
  - 若用户在启动实例时选择【自动生成密码】，则初始密码由系统随机分配。您可以登录[云平台控制台](http://console.tcecqpoc.fsphere.cn)，点击右侧站内信按钮，查收新购买的服务器页面中将包含云主机登录管理员帐号及初始密码。

  - 若用户在启动实例时选择了自定义密码，则密码为用户在购买云服务器实例时指定的密码。有关密码的更多内容，如忘记登录密码应该如何操作，请参考 [登录密码](/doc/product/213/6093)。

### 使用密钥登录的前提条件
**使用密钥登录到云服务器时需要创建并下载私钥。**
首先需要创建 SSH 密钥、下载私钥、绑定 Linux 云服务器。有关密钥操作的更多内容，请参阅 [SSH 密钥](/doc/product/213/6092)。

## 本地 Windows 计算机密码登录
### 登录工具
使用 **远程登录软件** ，采用密码登录 Linux 实例（本例中选择使用 PUTTY，用户也可以选择其他类型的登录软件）。
### 操作步骤
1. 安装 Windows 远程登录软件，参考下载地址：http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html

2. 使用 PUTTY 连接 Linux 云服务器。打开Putty客户端，在PuTTY Configuration 窗口中输入以下内容：
  >- Host Name：云服务器的公网 IP（登录 [云服务器控制台](http://console.tcecqpoc.fsphere.cn)，可在列表页及详情页中获取主机公网IP）。
  >- Port：云服务器的端口，必须填 22。（请确保云主机 22 端口已开放，详见查看 [安全组(/doc/product/213/5221) 及 [网络ACL](/doc/product/215/5132)）
  >- Connect type：选择“ SSH ”。

3. 输入完后，单击【Open】，创建一个新对话。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5d38a4ffbc.png)

4. 在 Putty 会话窗口中，输入前提条件中获得的管理员帐号，按回车键。再输入前提条件中获取的登录密码，回车完成登录过程。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5d47b8b5da.png)

>**注意：**
>如果登录失败，请检查您的云服务器实例是否允许 22 端口的入流量。端口的查看请参考 [安全组](/doc/product/213/5221) ,若您的云服务器处于 [私有网络](/doc/product/213/5227) 环境下，请同时查看相关子网的 [网络ACL](/doc/product/215/5132) 。 

## 本地 Windows 计算机 SSH 密钥登录
### 登录工具
使用 **远程登录软件** ，采用 SSH 密钥登录 Linux 实例（本例中选择使用 PUTTY，用户也可以选择其他类型的登录软件）。

### 操作步骤
1. 安装 Windows 远程登录软件，参考下载地址：http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html ，分别下载 putty.exe 及 puttygen.exe 两个文件。

2. 选择私钥。打开 puttygen.exe，单击【Load】按钮，在弹窗中首先进入您存放前提条件中下载下来的私钥的路径，然后选择“All File（\*.\*）”，选择下载好的私钥（例子中为文件david，david是密钥的名称），单击【打开】。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5c48fb810a.png)

3. 密钥转换。在 key comment 栏中输入密钥名，输入加密私钥的密码，单击【Save private key】，在弹窗中选择您存放密钥的目录，然后在文件名栏输入 密钥名 +".ppk"，单击【保存】按钮。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5c4ff657cc.png)

4. 打开 putty.exe ，进入【Auth】配置。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5c61c61e42.png)

5. 单击【Browse】按钮，打开弹窗后进入密钥存储的路径，并选择密钥，单击【打开】，返回配置界面，进入【Session】配置。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5c67ea3edb.png)

6. 在Session配置页中，配置服务器的IP，端口，连接类型。
 - IP：云服务器的公网IP。登录 [云服务器控制台](http://console.tcecqpoc.fsphere.cn)，可在列表页及详情页中获取主机公网IP。
 - 端口：云服务器的端口，必须填 22 。（请确保云主机22端口已开放，详见查看 安全组 及 网络ACL）。

6. 在【Saved Sessions】输入框中中输入会话名称（本例为 test ），再单击【Save】按钮，然后双击会话名称或者单击【Open】按钮发起登录请求。
  ![](http://imgcache.tcecqpoc.fsphere.cn/image/mccdn.qcloud.com/img56a5c6bca781f.png)

>**注意：**
>如果登录失败，请检查您的云服务器实例是否允许 22 端口的入流量。端口的查看请参考 [安全组](/doc/product/213/5221) ，若您的云服务器处于 [私有网络](/doc/product/213/5227) 环境下，请同时查看相关子网的 [网络ACL](/doc/product/215/5132) 。 

## 本地 Linux/Mac OS 计算机使用密码登录
### 登录工具
使用 Mac OS 系统自带的终端（Terminal）登录，SSH 方式。

### 操作步骤
1. Mac OS 用户请打开系统自带的终端（Terminal）并输入以下命令，Linux 用户请直接运行以下命令：	`ssh <username>@<hostname or ip address>` 
  (其中：`username`即为前提条件中获得的管理员帐号， `hostname or ip address`为您的 Linux 实例公网 IP 或 自定义域名）

2. 输入前提条件中获得的密码（此时仅有输入没有显示输出），回车后即可完成登录。

>**注意：**
>如果登录失败，请检查您的云服务器实例是否允许 22 端口的入流量。端口的查看请参考 [安全组](/doc/product/213/5221) ，若您的云服务器处于 [私有网络](/doc/product/213/5227) 环境下，请同时查看相关子网的 [网络ACL](/doc/product/215/5132) 。 


## 本地为 Linux/Mac OS 使用密钥登录
### 登录工具
使用 Mac OS 系统自带的终端（Terminal）登录。

### 操作步骤
1. Mac OS 用户请打开系统自带的终端（Terminal）并输入以下命令，Linux 用户请直接运行以下命令，赋予私钥文件仅本人可读权限。`chmod 400 <下载的与云服务器关联的私钥的绝对路径> `

2. 运行以下远程登录命令：`ssh -i "<下载的与云服务器关联的私钥的绝对路径>" <username>@<hostname or ip address>。`
  (其中：`username`即为前提条件中获得的管理员帐号， `hostname or ip address`为您的 Linux 实例公网 IP 或 自定义域名。例如：`ssh -i "Mac/Downloads/shawn_qcloud_stable" ubuntu@119.xxx.xxx.xxx`）。

>**注意：**
>如果登录失败，请检查您的云服务器实例是否允许 22 端口的入流量。端口的查看请参考 [安全组](/doc/product/213/5221) ，若您的云服务器处于 [私有网络](/doc/product/213/5227) 环境下，请同时查看相关子网的 [网络ACL](/doc/product/215/5132) 。 