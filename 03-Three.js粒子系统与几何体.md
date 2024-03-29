#### **粒子系统**
* 粒子系统

```

模拟雨滴和雪花
三维效果
使用CanvasRenderer 可以直接使用THREE.Particle对象
使用WebGLRenderer 使用THREE.Sprite
使用ParticleSystem类来显示 几何体 + 材质
用来创建大量粒子
ParticleSystem:FrustrumCulled 落在相机可见范围外的粒子不被渲染 
ParticleCanvasMaterial canvas画布内容作为纹理
ParticleBasicMaterial 贴图
```


 * 精灵 THREE.Sprite
 
```

HUD Head-Up display 平视显示器
基于屏幕坐标移动，定位和移动的对象
相当于蒙上一层
广告牌 总是面向镜头
```


* 注意点
	* [Blender](https://www.blender.org/)
	
```

粒子来自于几何体的顶点
三维建模工具

blender导入three扩展
自己作死 要先进user pre先激活
3D Studio Max
测试性的材质来检测, 用js控制台输出材质信息
```


* 几何体
	* [wiki](http://en.wikipedia.org/wiki/Torus_knot)
	
```

平面 PlaneGeometry
水平放置 将这个网格沿x轴向后旋转四分之一圈
mesh.rotation.x = -Math.PI/2;
圆形 CircleGeometry
塑形 ShapeGeometry
自定义二维图形
shape对象和shapeGeometry
shape的辅助函数
立方体 CubeGeometry
球体 SphereGeometry
圆柱 CylinderGeometry
圆环 TorusGeometry
arc
环面纽结 TorusKnotGeometry

p q
多面体 PolyhedronGeometry
多面体 = 平面 + 直边
vertices faces
radius detail
二十面体 IcosahedronGeometry
八面体 OctahedronGeometry
四面体 TetraHedronGeometry
```



* 复杂几何体
	* [typeface.js](http://typeface.neocracy.org/)提供的字体
	
```

凸面体 ConvexGeometry
凸包就是包围这组点的最小图形
扫描面 LatheGeometry
拉伸几何体 ExtrudeGeometry
管状体 TubeGeometry
参数几何体 ParametricGeometry
u v 越大越光滑
function
slices 定义u分成多少份
stacks 定义v分成多少份
useTris 默认false四边形
克莱因瓶 平面 3d莫比乌斯带...
文本几何体 TextGeometry
添加自定义字体
TrueType/OpenType → js库
```


* 二元操作组合网格
	* THREE扩展库[THREEBSP](https://github.com/skalnik.ThreeBSP)
	
```

coffee-script 咖啡脚本 更友好的js变体
也可以不用已经编译好的js

<script type="text/coffeescript">
onReady();
</script>

function onReady() { THREE.js code }

使用未经组合的网格
intersect 相交
union 联合
subtract 相减
```


* 几何体组合和合并
* 从外部资源中加载几何体
	*   [蛋白质数据银行](http://www.rcsb.org/)
	
```

// 格式
JSON
OBJ 和 MTL(一般一起使用,材质定义在OBJ中)
Collada 定义XML类文件中数字内容的格式
STL 快速成型 三维打印
THREE有STLExporter.js 导出
CTM 压缩存储表示三维网格的三角形面片
VTK 指定顶点和面 Three.js支持ASCII
PDB 定义蛋白质的形状
PLY 保存三维扫描仪的数据
GeometryExporter.js
SceneExporter.js 导出的JSON明确描述了物体光源场景等信息
```

