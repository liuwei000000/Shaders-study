# Shaders-study

https://thebookofshaders.com/  
https://github.com/patriciogonzalezvivo/thebookofshaders  
http://editor.thebookofshaders.com/  
https://www.shadertoy.com/results?query=&sort=hot&from=24&num=12  
https://github.com/DanRuta/webassembly-webgl-shaders    
https://github.com/KhronosGroup/glTF-Sample-Viewer  
https://www.khronos.org/files/webgl20-reference-guide.pdf  
https://github.com/nickjanssen/PatrolJS  
https://github.com/mrdoob/three.js  

水  
https://www.html5tricks.com/demo/webgl-water/index.html  
风  
http://www.bongiovi.tw/experiments/webgl/blossom/  



地理矢量数据  
https://www.nextzen.org/  
https://github.com/3dcitydb/3dcitydb-web-map  

地球库：  
OpenWebGlobe   
https://github.com/OpenWebGlobe/WebViewer  
NASAWorldWind  
https://github.com/NASAWorldWind/WebWorldWind  
cesium  
https://github.com/Miaosen1202/cesium.git  
itowns  
https://github.com/iTowns/itowns  

3D运算库
https://github.com/evanw/csg.js  

LOD
https://threejs.org/examples/#webgl_modifier_simplifier   
https://github.com/jpbetz/synthesis.js?files=1  
https://github.com/google/draco

Continous Distance-Dependent LOD (CDLOD) http://vertexasylum.com/2010/07/11/oh-no-another-terrain-rendering-paper/  
GPU Based Geomety Clipmaps (GPUGCM)  http://hhoppe.com/gpugcm.pdf  
Chunked LOD http://tulrich.com/geekstuff/sig-notes.pdf  
使用OpenGL GPU Tessellation渲染Terrains(书：OpenGL Insight,第10章)   
Geometrical MipMapping https://www.flipcode.com/archives/article_geomipmaps.pdf   

每个都提供了一种渲染地形的独特方式,例如,CDLOD使用着色器(GLSL或HLSL)非常容易实现,但也能够在CPU上实现(对于传统硬件)但是Planet Rendering的目标是爆炸最好使用现代GPU,因此当您想要挤压GPU时,GPUGCM是最好的.它们都可以很好地处理基于数据,程序或混合(基于固定数据或高度图的地形以及添加了程序性工作的细节)渲染大地形.  
此外,存在基本几何剪贴图方法的球面扩展,但存在一些问题,因为高度图的平面样本必须使用球面坐标进行参数化.  
另一方面,Chunked LOD非常适合传统硬件,不需要任何GPU端计算,它适用于大型数据集,但无法实时处理程序数据(可能需要进行一些修改)  
使用Tessellation着色器是另一种技术,非常新,因为OpenGL 4.x问世,在我看来它可能是最好的,但是,我们谈论的是Planet Rendering,我们遇到的问题是其他方法可以很容易处理,它是关于精度.  
除非您只希望精度在verticies之间为1Km,否则请选择Tessellation着色器.使用这种方法真正大地形的问题是抖动有点难以解决(至少对我而言,因为我是曲面细分着色器的新手).  
Geomipmapping是一项很棒的技术,利用了四叉树并且投影像素误差很小,但是,对于行星渲染,您需要设置至少16级细节,这意味着您需要(用于拼接pourposes)一些额外的补丁到连接不同级别并照顾邻居的级别,这可能很难解决,尤其是使用6个地形面.  
还有另一种方法,非常特别：“Projective Grid Mapping for Planetary Terrain”非常适合可视化,但有其缺点,如果你想了解更多,请转到链接.  
 
