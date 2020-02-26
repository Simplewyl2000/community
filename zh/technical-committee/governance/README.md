# SIG  管理指南

 目录

- [申请新SIG流程](#id1)
- [SIG变更批准流程](#id2)
  - [增删新项目或repository申请流程](#id2-1)
  - [修改SIG章程申请流程](#id2-2)
  - [变更团队成员申请流程](#id2-3)



<h2 id="id1">申请新SIG流程</h2>

说明：

所有openEuler社区的SIG都必须有一个章程（Charter）来明确SIG的范围和治理规则。

+ 范围必须明确定义SIG负责指导和维护的领域
+ 治理规则必须说明SIG中的职责，以及拥有这些职责的角色和工作开展方式



具体的申请流程如下：

**1、使用SIG模板创建自己的新SIG**

将 gitee.com/openeuler/community Fork到你的Gitee下。并在sig目录下创建你的sig文件夹，以及把SIG申请模板拷贝到该文件夹下。


```
git clone https://gitee.com/YOURGITEE/community

cd ./community/sig

cp -r sig-template sig-YOURSIGNAME

cd sig-YOURSIGNAME

```

**2、完成新SIG章程的填写**

为便于更好的理解和填写[SIG申请模板](./../../../sig/sig-template/sig-template_cn.md)里的内容，建议先阅读[建议书和要求](./SIG-governance-requirements.md)，完成新SIG的申请填写。

```
mv sig-template_cn.md sig-YOURSIGNAME_cn.md

mv sig-template.md sig-YOURSIGNAME.md

vi sig-YOURSIGNAME_cn.md

vi sig-YOURSIGNAME.md

```

**3、完成新SIG成员的配置**

请在OWNERS文件中完成对SIG成员的配置

```
vi OWNERS

```

**4、完成新SIG的Repository的配置**

请参考[openEuler的Repository说明](/zh/Gitee-Management/Gitee-management-guide.md)，完成SIG所拥有的Repository的配置。

- 如果您的项目在openEuler社区只维护软件包，请点击[src-openeuler.yaml](/repository/src-openeuler.yaml)，在其中按照格式把你的项目添加进来。

```
vi ../../repository/src-openeuler.yaml

```

- 如果不是以上的情况，请单击[openeuler.yaml](/repository/openeuler.yaml)，并按照内部的格式在文件的最后把您的SIG添加进来

```
vi ../../repository/openeuler.yaml

```

**5、在sig文件夹的sig.yaml内添加新SIG的相关信息**

根据以上的信息，打开sig文件夹下[sigs.yaml](/sig/sigs.yaml)文件，在末尾添加新sig的相关信息并提交PR。

```
vi ../sigs.yaml

- name: sig-YOURSIGNAME
  repositories:
  - openeuler/aaa
  - src-openeuler/bbb
```

**6、完成SIG的README初稿信息**

一个sig的README是这个团队给贡献者们了解本团队的第一手资料。所以每一个sig团队都应该提供README里的相关信息。请按照README模板完成对sig团队的介绍

```
vi README.md
```

**7、提交PR**

将以上修改提交到Gitee上，并在Gitee上创建一个Pull Request。

**8、向TC发送邮件申请**

给技术委员会发邮件（邮箱<tc@openeuler.org>），并在正文中包含主题“[*新SIG提案]*”和PR的链接

**9、TC评审并反馈意见**

技术委员会通常会在发送申请后的一周内反馈。如果遇到假期或重要会议等因素，可能会需要更长时间。在此期间，您可以进行任何有需要的更改

**10.TC评审通过并合入**

技术委员会将通过合并Pull Request的方式来批准您的申请





<h2 id="id1">SIG变更申请流程</h2>

如果您要修改SIG章程（charter.md）、团队成员(OWNERS)、增删Repository(Repository)等，您需要提交SIG变更批准流程。

<h3 id="id2-1">增删新项目或repository申请流程</h3>

**1、完成新项目的Repository的配置或删除相关配置**

请参考[openEuler的Repository说明](/zh/Gitee-Management/Gitee-management-guide.md)，完成SIG所拥有的Repository的配置。

- 如果您的项目在openEuler社区只维护软件包，请点击[src-openeuler.yaml](/repository/src-openeuler.yaml)，在其中按照格式对你的项目的repository进行添加/删除。

```
vi ../../repository/src-openeuler.yaml

```

- 如果不是以上的情况，请单击[openeuler.yaml](/repository/openeuler.yaml)，在其中按照格式对你的项目的repository进行添加/删除。。

```
vi ../../repository/openeuler.yaml

```

**2、在sig文件夹的sig.yaml内添加新项目的repository信息或删除相关信息**

根据以上的信息，打开sig文件夹下[sigs.yaml](/sig/sigs.yaml)文件，在`name`字段下面找到项目所属的sig，可以在该sig的`repositories`的末尾添加项目的repository，或者找到待删除的repository进行删除。

```
vi ../sigs.yaml

- name: sig-YOURSIGNAME
  repositories:
  - openeuler/aaa
  - src-openeuler/bbb
```

**3、刷新README**

根据新增的项目和其repository，请同步刷新README内的“项目清单”下内容，便于大家查找

```
vi README.md
```

**4、提交PR**

将以上修改提交到Gitee上，并在Gitee上创建一个Pull Request。

**5、向TC发送邮件申请**

给技术委员会发邮件（邮箱<tc@openeuler.org>），并在正文中包含主题“[*增删repository提案]*”和PR的链接

**6、TC评审并反馈意见**

技术委员会通常会在发送申请后的一周内反馈。如果遇到假期或重要会议等因素，可能会需要更长时间。在此期间，您可以进行任何有需要的更改

**7.TC评审通过并合入**

技术委员会将通过合并Pull Request的方式来批准您的申请



<h3 id="id2-2">修改SIG章程申请流程</h3>

#### 重大变更申请流程

待修改的sig章程涉及到**重大的变更**，或可能影响到其他sig，需要提交给技术委员会审核，请采用以下流程：

**1、修改SIG章程**

请在`/community/sig`文件夹下找到您的sig文件夹，完成sig文件夹的修改

```
vi sig-YOURSIGNAME_cn.md

vi sig-YOURSIGNAME.md

```

**2、刷新README**

请视需要，根据修改的章程同步刷新README内的“项目清单”下内容，便于大家了解

```
vi README.md
```

**3、提交PR**

将以上修改提交到Gitee上，并在Gitee上创建一个Pull Request。

**4、向TC发送邮件申请**

给技术委员会发邮件（邮箱<tc@openeuler.org>），并在正文中包含主题“[*修改SIG章程提案]*”和PR的链接

**5、TC评审并反馈意见**

技术委员会通常会在发送申请后的一周内反馈。如果遇到假期或重要会议等因素，可能会需要更长时间。在此期间，您可以进行任何有需要的更改

**6.TC评审通过并合入**

技术委员会将通过合并Pull Request的方式来批准您的申请。并会通知收影响的其他SIG。



**对于重大变更的操作说明**，为了加快重大变更的申请审批速度，可以采取以下方式：

+ 从SIG组中确定推动变更的负责人，最常见的就是SIG的Mainatiner作为负责人
+ 变更所有者组织SIG组成员一起制定变更内容，并与技术委员会讨论（为便于信息同步，可以在与指导委员会的沟通中键入SIG组的邮件列表）





#### 内部变更申请流程

**只影响本SIG范围内的变更**，只需要SIG内的Maintainer达成一致，请走以下流程

**1、修改SIG章程**

请在`/community/sig`文件夹下找到您的sig文件夹，完成sig文件夹内SIG章程的修改

```
vi sig-YOURSIGNAME_cn.md

vi sig-YOURSIGNAME.md

```

**2、刷新README**

请视需要，根据修改的章程同步刷新README内的“项目清单”下内容，便于大家了解

```
vi README.md
```

**3、提交PR**

将以上修改提交到Gitee上，并在Gitee上创建一个Pull Request。

**4、在SIG内部发送邮件申请**

给您所对应的sig团队的邮箱列表发邮件申请，可以在正文中包含主题“[*修改SIG章程提案]*”和PR的链接。如果之前在SIG团队内对此变更已经有讨论，可以省略该步骤

**5、SIG内部评审并给出意见**

如果您的SIG内部已经有评审意见，可以省略该步骤。

**6.TC评审通过并合入**

SIG的Maintainer合并Pull Request来批准申请。



<h3 id="id2-3">变更团队成员申请流程</h3>

团队成员的刷新由SIG内部自己维护

**1.完成新SIG成员的配置**

请在`/community/sig`文件夹下找到您的sig文件夹，完成sig文件夹内SIG章程的修改，在OWNERS文件中完成对SIG成员的配置

```
vi OWNERS

```

**2、刷新README**

请视需要，根据修改的章程同步刷新README内的“项目清单”下内容，便于大家了解

```
vi README.md
```

**3、提交PR**

将以上修改提交到Gitee上，并在Gitee上创建一个Pull Request。

**4、在SIG内部发送邮件申请**

给您所对应的sig团队的邮箱列表发邮件申请，可以在正文中包含主题“[*修改SIG章程提案]*”和PR的链接。如果之前在SIG团队内对此变更已经有讨论，可以省略该步骤

**5、SIG内部评审并给出意见**

如果您的SIG内部已经有评审意见，可以省略该步骤。

**6.TC评审通过并合入**

SIG的Maintainer合并Pull Request来批准申请。




