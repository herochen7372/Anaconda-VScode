# 导出 / 导入 conda 环境

Python 项目对软件包的版本 非常敏感。当我们最终决定将某个开源的 Python 项目上传到 Github 时，应当明确地声明项目的各种依赖包以及版本号信息，否则其他人将很难顺利地运行我们的代码。

首先，conda 本身可以通过将环境整体导入导出的方式解决问题。现在假设已经进入到了 py3env 环境下，我们可以通过以下命令将当前环境的各种依赖信息以文本形式导出，注意拓展名必须是 *.txt，*.yaml，*.yml 的其中一个。

conda env export > imports.yml

再假设在另一个机器安装好了 conda。在另一个机器创建新环境时可以通过 -f 选项将依赖文件所记载的环境名，依赖包及版本号，镜像源全部导入进来。

conda env create -f imports.yml

第二种方式是通过 pip 工具导入 / 导出项目依赖 ( 比如有些机器不用 conda 管理环境 )。pip 是一个专门下载并管理 Python 依赖库的工具，conda 总是会将它内置到各个环境下。每个环境下的 pip 只管理当前环境的依赖。使用 pip 导出的依赖文件约定上以 requirements.txt 来命名。

pip list --format=freeze > requirements.txt

    网上大部分推荐的是 pip freeze 命令。在此不直接这么做的原因，见：pip freeze 导出含有路径 (@ file:///) 问题小记-CSDN博客

同样地，这份文件可以被其它环境下的 pip 工具导入进去：

pip install -r requirements.txt

仅从下载依赖这一功能上看，conda 和 pip 有一点重合，但是使用 conda 进行依赖管理要比 pip 更加方便。只是对于部分 Python 依赖，conda 可能无法安装，这时候可以再去尝试用 pip 进行安装。

   



