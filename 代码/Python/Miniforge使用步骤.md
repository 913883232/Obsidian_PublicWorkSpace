Conda命令行：
环境列表：conda info -e | conda env list
添加镜像地址：conda config --add channels https://pypi.tuna.tsinghua.edu.cn/simple
查看镜像地址：conda config --show-sources
删除镜像地址：conda config --remove channels https://pypi.tuna.tsinghua.edu.cn/simple
创建虚拟环境：conda create -n my_env python=3.12.5
激活虚拟环境：windows：conda activate env_name；linux：source activate env_name
退出虚拟环境：windows：conda deactivate；linux：source deactivate env_name
删除虚拟环境：conda remove -n env_name --all

打开Miniforge Prompt