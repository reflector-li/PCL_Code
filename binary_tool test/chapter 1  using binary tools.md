# chapter 1  using binary tools 

## 二进制文件存放路径：usr/bin

## 1. pcl_view 使用

- -cam(*)：修改初始视角的相机参数，格式为

  ```
   -cam [Clipping Range / Focal Point / Position / ViewUp / Distance / Field of View Y / Window Size / Window Pos]
  ```

  参数分别代表：剪切范围/ 焦点/位置/视角/距离/视场Y/窗口大小/窗口位置

  也可以直接打开文件，可以使用pcl_viewer  打开pcd文件后使用ctr+s保存当前视角的相机参数.cam文件。

  ```
  -cam wolf.cam
  ```

  最后使用pcl_viewer工具命令：

  ```
  pcl_viewer  wolf.pcd -cam wolf.cam 
  
  pcl_viewer  wolf.pcd -cam 197.814,456.977/-13.5813,22.5211,48.5076/-313.405,-60.8872,73.5552/0.0602031,0.0823253,0.994785/0.523599/960,540/77,95
  ```

  

- -multiview 0/1：多个视图同时查看，其中0表示在同一个窗口，1表示在不同窗口。

  ```
  pcl_viewer -multiview 1    wolf.pcd   Horse.pcd
  
  pcl_viewer -multiview 0   wolf.pcd   Horse.pcd
```
  
  注意，其中前景色/点大小/透明度可以分别设置。例如：
  
  ```
  pcl_viewer -multiview 1 Horse.pcd -fc 255,0,0 wolf.pcd -fc 0,125,0
  ```
  
  

- -normals 0/X ：禁用/启用每个Xth点的表面法线显示为线（默认禁用），X表示正常的单位矢量大小（默认为 0.02）。
- -pc 0/X：禁用/启用将第X个点的主曲率显示为线（默认禁用），X表示将主曲率大小（默认为0.02）。



## 2.pcl_convert_pcd_ascii_binary 可以进行精度转换

```
pcl_convert_pcd_ascii_binary wolf.pcd wolf_bin.pcd 0 0.1
```

​    最后数字表示转换精度。



## 3.pcl_mesh2pcd 无法将ply文件转换为pcd文件

![报错图片](/home/reflector/sambashare/2021-02-23 20-45-05屏幕截图.png)

解决方法：使用 pcl_ply2pcd

```
pcl_ply2pcd New_Qlone.ply new_from_ply.pcd
```

