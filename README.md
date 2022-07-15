# three-cube

 ![image](https://user-images.githubusercontent.com/83756058/179190246-ad6c4e13-da6a-401b-a824-55c0908f4cc5.png)


## 一、引入three.js

1、npm 引入（需安装npm, 安装three, 不需要单独引入loader等）。

2、通过外部cdn链接直接引入（直接html起步，简单一把梭，需单独引入loader, model, controls等）。

## 二、创建场景scene

1、创建场景
```
const scene = new THREE.Scene();
```

2、可以设置background和environment.

3、接下来所有的object都需要添加在scene中。

## 三、创建相机camera

1、相机类型有

*   [PerspectiveCamera](https://threejs.org/docs/api/zh/cameras/PerspectiveCamera.html)(常用)
*   [CubeCamera](https://threejs.org/docs/api/zh/cameras/CubeCamera.html)
*   [OrthographicCamera](https://threejs.org/docs/api/zh/cameras/OrthographicCamera.html)
*   ...

2、创建相机
```
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 1000);

camera.position.set(0, 0, 10);
```
## 四、创建渲染器renderer

1、创建渲染器
```
const renderer = new THREE.WebGLRenderer({antialias:true});

renderer.setSize(window.innerWidth, window.innerHeight);
```

2、放入场景和相机，并挂载到HTML上。

```
renderer.render(scene, camera);

document.body.appendChild(renderer.domElement);
```

## 五、添加object

1、three.js中有很多元素可以添加，比如Line,Geometry, Helper, light ,还可以引入图片或者模型model(需要loader).

## 六、动画animation

1、
```
requestAnimationFrame(animation);
```

2、

```
renderer.setAnimationLoop( animation );
```

## 七、踩过的坑

1、主体script需添加type="module", 不然不起作用。
```
<script type="module">
```

2、要在html里直接使用three.js，需要添加importmap
```
<script type="importmap">
        {
            "imports": {
                "three": "../node_modules/three/build/three.module.js"
            }
        }
</script>
```

3、安装live preview扩展，创建本地服务器，解决跨域问题。
