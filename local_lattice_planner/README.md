# grid_path_searcher


## 1. 介绍

该仓库主要是对local state planner算法进行复现。

**具有以下功能：**

- 可以通过Rviz选择目标点，然后采样生成lattice路径；
- 具有前端采样轨迹搜索，到后端光滑轨迹生成功能（to do）。

**功能包介绍：**

- map_generator：主要用来生成随机的地图
- path_searcher：用于路径搜索，目前只实现了一帧lattice planner 
- waypoint_trajectory_generator：通过Rviz插件生成三维的lattice轨迹

## 2. 编译
我的开发环境为：`Ubuntu 18.04`、`Ros melodic`

```shell
mkdir local_lattice_planner_ws/src && cd local_lattice_planner_ws/
catkin_make -j8
```

## 3. 运行

**通过Rviz生成轨迹**

```shell
source devel/setup.bash
roslaunch grid_path_searcher demo.launch
```

运行之后，会自动打开Rviz，并自动加载插件。

使用方法：点击`3D Nav Goal`按钮，然后鼠标左键点击Rviz中的位置，左键不松，继续点击右键控制箭头的高度，将自动生成lattice路径。


> 在使用rviz显示时出现rviz卡死的现象，在我的开发环境中也有发现此问题，主要是NVIDIA驱动的原因，建议关闭独立显卡驱动，使用集成显卡显示rviz，即可正常运行。

> 致谢：在学习路径规划的过程中，浙江大学的高飞老师给了我很多的帮助，其中也参考了他的不少代码和课件，在此向他提出感谢！
