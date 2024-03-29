#### **材质**
* 材质
	* [例子](https://www.shadertoy.com/view/4dXGR4)
	
```

网格基础材质 MeshBasicMaterial
网格深度材质 MeshDepthMaterial 网格到相机的距离
逐渐消失的效果
wireframe wireframeLinewidth
设置cameraNear
设置cameraFar 超出可见距离看不见
网格法向材质 MeshNormalMaterial
决定光的反射方向
THREE.FlatShading 平面着色
THREE.SmoothShading 平滑着色
网格面材质 MeshFaceMaterial
网格朗伯材质 MeshLambertMaterial 光照 不光亮物体
ambient 环境色
emissive 材质发射的颜色 不是光源 不受其他光照影响
网格Phong式材质 MeshPhongMaterial 光照 光亮物体
ambient emissive
specular 镜面的 金属/塑料质感
shininess 高光部分的亮度
着色器材质 ShaderMaterial 自定义 顶点
属性...
直线基础材质 LineBasicMaterial 直线几何体
虚线材质 LineDashedMaterial 同上
短划线长度
短划线中间空格长度
必须调用computeLineDistances()
```


* 材质属性

```

基础属性
融合属性 与背景的融合
高级属性 控制底层webgl上下文渲染物体
```


*  纹理

```

二维高频细节
几何建模限制
环境纹理映射 Enviroment mapping
环境包装盒和曲面法向之间的映射
纹理空间 物体空间 纹理坐标 ==> 函数映射
```


* 材质

```

color = Normal
Normal = color 贴图
```


* UV工具 美工
* 纹理

```

凹凸贴图和法线贴图 添加深度和细节 后者更细致
光照贴图 假阴影 静态场景
环境贴图 材质上的反光细节
创建一个CubeMap对象 6个纹理的集合
创建一个带有这个CubeMap对象的方块
将CubeMap作为纹理
高光贴图 让网格的某些部分变得光亮
修改网格的UV贴图 对贴图进行微调
HTML5画布和视频元素作为纹理输入
```


* 纹理的用法

```

定义网格的颜色
高光 + 凹凸 + 反光
```


* 注意
	* [关于UV贴图](http://stackoverflow.com/questions/15137695/three-js-lightmap-causes-an-error-webglrenderingcontext-gl-error-gl-invalid-op)
    * [环境贴图示例图片来源](http://www.humus.name/index.php?page=Textures)
    
```

最好使用正方形图片 ∵mipmap
256 x 256, 512 x 512, 1024 x 1024
等待纹理加载完成

texture = THREE.ImageUtils.loadTexture('texture.png', {},
0020function() { renderer.render(scene); }); // ??

magFilter LinearFilter
minFilter LinearMipMapLinearFilter

计算环境反光特别耗费CPU 光线追踪法

最好的效果往往是用低光亮度实现的
高光贴图还会受到光照的影响
```


* 纹理的高级用途
	* [literally库](http://literallycanvas.com/) 创建交互式的画布
	+ [Perlin噪音](https://github.com/wwwtyro/perlin.js)
	
```

定制UV映射 指定哪一部分显示在物体表面
图片加载是异步的 渲染循环 回调函数
纹理的repeat属性 包裹属性 ClampToEdgeWrapping → RepeatWrapping
```


* 渲染后期处理

```

基本后期处理通道
BloomPass 泛光通道 和 FilmPass 胶片通道
掩码
TexturePass 纹理通道 保存渲染结果
ShaderPass 着色器通道
eg.褐色滤镜 镜像效果 颜色调整
模糊效果 更高级的滤镜
开发一个简单的着色器，来创建自定义的后期处理效果
步骤
创建EffectComposer对象 在对象上添加后期处理通道
在render循环中使用EffectComposer渲染场景
HorizontalTiltShiftShader 移轴
定制灰度图着色器
vertexShader 调整每个顶点的位置
fragmentShader 决定每个像素的颜色
定制位着色器
```


* 后期处理通道

```

BloomPass
DotScreenPass 一层黑点
FilmPass 电视屏幕
MaskPass 掩膜
RenderPass
SavePass
ShaderPass
TexturePass
```


* basic-vertex-shader

```

Use this as displacement:
Base example on [this](http://aerotwist.com/tutorials/an-introduction-to-shaders-part-2/)
Show this as [example](http://www.clicktorelease.com/code/perlin/explosion.html)
```


* basic-fragment-shader

```
Create something like this:

// pass in mouse as uniforms
// pass in resolution?


#ifdef GL_ES
precision mediump float;
#endif

uniform float time;
uniform vec2 mouse;
uniform vec2 resolution;

void main( void ) {

vec2 position = ( gl_FragCoord.xy / resolution.xy ) + mouse / 4.0;

float color = 0.0;
color += sin( position.x * cos( time / 15.0 ) * 80.0 ) + cos( position.y * cos( time / 15.0 ) * 10.0 );
color += sin( position.y * cos( time / 10.0 ) * 40.0 ) + cos( position.x * sin( time / 25.0 ) * 40.0 );
color += sin( position.x * sin( time / 5.0 ) * 10.0 ) + sin( position.y * sin( time / 35.0 ) * 80.0 );
color *= sin( time / 10.0 ) * 0.5;

gl_FragColor = vec4( vec3( color, color * 0.5, sin( color + time / 3.0 ) * 0.75 ), 1.0 );

}
```

* 后期处理注意

```

不是所有通道的结果都会输出到屏幕
效果组合器添加通道的顺序很重要
重用某个EffectComposer,可以使用TexturePass
EffectComposer有多个RenderPass clear设为false
```


*  Physijs 添加物理效果
  + [Physijs](http://chandlerprall.github.io/Physijs/)
  + 另一个著名的物理引擎 [ammo.js]( https://github.com/kripken/ammo.js/)
  + [网页线程web workers](https://html.spec.whatwg.org/multipage/workers.html)
  
```

后台线程中执行计算
  
Physijs只是ammo.js的一个包装器
Cannon.js
Physijs的基础图形
PlaneMesh 厚度为0的平面
BoxMesh 类似方块的几何体
SphereMesh 球形
CylinderMesh 上下一致的圆柱体
ConeMesh
CapsuleMesh 胶囊网格
ConvexMesh 凸包网格
ConcaveMesh 比上面细致 但性能影响极大
HeightfieldMesh 高度场网格
使用约束限制对象移动
PointConstraint 限制两点间的移动
HingeConstraint 活页/门
SliderConstraint 将移动限制到一个轴
ConeTwistConstraint 球销 移动受一系列角度限制
DOFConstraint 实现细节的控制
_dirtyPosition _dirtyRotation
```


* OBJ文件

```

基于ASCII的三维静态模型存储格式
包含信息，顶点坐标，面数组，纹理坐标，材质文件
```
