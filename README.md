# 《Unity Shader入门精要》源代码

本项目是书籍《Unity Shader入门精要》的配套源代码。最新版本请移步<a href="https://github.com/candycat1992/Unity_Shaders_Book" target="_blank">本项目的Github页面</a>。

我们推荐您从Github上clone项目源码并及时检查更新。如果下载速度过慢可以移步<a href="http://pan.baidu.com/s/1pLndw2R" target="_blank">百度网盘地址</a>。

纸质版书籍可在以下链接购买：<a href="https://www.amazon.cn/Unity-Shader%E5%85%A5%E9%97%A8%E7%B2%BE%E8%A6%81-%E5%86%AF%E4%B9%90%E4%B9%90/dp/B01G95GMU6/ref=sr_1_1?s=books&ie=UTF8&qid=1464607131&sr=1-1&keywords=unity+shader%E5%85%A5%E9%97%A8%E7%B2%BE%E8%A6%81" target="_blank">亚马逊</a>、<a href="http://product.dangdang.com/23972910.html" target="_blank">当当</a>、<a href="http://item.jd.com/11927199.html" target="_blank">京东</a>

# 随书彩图

我们提供了包含书中所有插图的彩色版插图集锦：<a href="http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_images.html" target="_blank">HTML</a>，<a href="http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_images.pdf" target="_blank">PDF</a>。

# 第四章勘误

由于数学章是全书的重要基础，我们决定把第四章公开，来及时让读者获取最新的第四章数学章的内容：<a href="http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_chapter_4.pdf" target="_blank">PDF</a>。

**注意**：我们可能会根据读者勘误随时更新该文档，内容和页号可能会与读者手中的版本不同，实体书中的勘误会在每次重印时进行修正。

# 读者反馈和勘误

尽管我们在本书的编写过程中多次检查内容的正确性，但不可避免书中仍然会出现一些错误，欢迎读者批评指正。任何关于本书内容、源码等方面的问题，欢迎读者反映到本书源码所在的<a href="https://github.com/candycat1992/Unity_Shaders_Book/issues" target="_blank">Github讨论页</a>，也可以发邮件（lelefeng1992@gmail.com）联系笔者。

关于目前**已发现的错误**我们会及时在网上更新：<a href="http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_corrigenda.html" target="_blank">勘误列表</a>。

我们也维护了读者反馈的问题列表：<a href="http://candycat1992.github.io/unity_shaders_book/unity_shaders_book_faq.html" target="_blank">FAQ</a>。

# Unity版本

我们**推荐使用Unity 5.0以上的版本来编译本项目**。如果你打算**使用更低版本的Unity，那么在学习本书时可能就会遇到一些问题**：

* 你可能发现会有些菜单或变量在你的Unity中找不到，这可能就是由于Unity版本不同造成的。绝大多数情况下，本书的代码和指令仍然可以工作良好，但在一些特殊情况下，Unity可能会更改底层的实现细节，造成同样的代码会得到不一样的效果（例如，在非统一缩放时对法线进行变换）。

* 还有一些问题是Unity提供的内置变量、宏和函数，例如我们在书中经常会使用UnityObjectToWorldNormal内置函数把法线从模型空间变换到世界空间中，但这个函数是在Unity 5中才被引入的，因此如果读者使用的是Unity 5之前的版本就会报错。类似的情况还有和阴影相关的宏和变量等。

* 和Unity 4.x版本相比，Unity 5.x最大的变化之一就是很多以前只有在专业版才支持的功能，在免费版也同样提供了。因此，如果读者使用的是Unity 4.x免费版，可能会发现本书中的某些材质会出错。

## 升级Unity 5.4

Unity 5.4对Shader部分进行了一些比较大的更新，最明显的一个特征是使用了unity_XXX来代替原有的XXX变换矩阵，例如_Object2World被替换成了unity_ObjectToWorld，_World2Object被替换成了unity_WorldToObject（均在UnityShaderVariables.cginc文件中被声明）。如果你打算直接使用Unity 5.4来编译本项目，Unity会自动更新相应的Shader，因此仍然不会报错。但在学习本书时，读者需要注意代码中一些由于自动更新造成的变化。

# 使用说明

本书源码的组织方式大多按资源类型和章节进行划分，主要包含了以下关键文件夹：

| 文件夹 | 说明 | 
| ------------- |:-------------| 
|Assets/Scenes|包含了各章对应的场景，每个章节对应一个子文件夹，例如第七章所有场景所在的子文件夹为Assets/Scenes/Chapter7。每个场景的命名方式为Scene_章号_小节号_次小节号，例如7.2.3节对应的场景名为Scene_7_2_3。如果同一个小节包含了多个场景，那么会使用英文字母作为后缀依次表示，例如7.1.2节包含了两个场景Scene_7_1_2_a和Scene_7_1_2_b。|
|Assets/Shaders|包含了各章实现的Unity Shader文件，每个章节对应一个子文件夹，例如第七章实现的所有Unity Shader所在的子文件夹为Assets/Shaders/Chapter7。每个Unity Shader的命名方式为ChapterX-功能，例如第七章使用渐变纹理的Unity Shader名为Chapter7-RampTexture。|
|Assets/Materials|包含了各章对应的材质，每个章节对应一个子文件夹，例如第七章所有材质所在的子文件夹为Assets/ Scenes/Chapter7。每个材质的命名方式与它使用的Unity Shader名称相匹配，并以Mat作为后缀，例如使用名为Chapter7-RampTexture的Unity Shader的材质名称是RampTextureMat。|
|Assets/Scripts|包含了各章对应的C#脚本，每个章节对应一个子文件夹，例如第五章所有脚本所在的子文件夹为Assets/Scripts/Chapter5。|
|Assets/Textures|包含了各章使用的纹理贴图，每个章节对应一个子文件夹，例如第七章使用的所有纹理所在的子文件夹为Assets/Textures/Chapter7。|

除了上述文件夹外，源码中还包含了一些辅助文件夹，例如Assets/Editor文件夹中包含了一些需要在编辑器状态下运行的脚本，Assets/Prefabs文件夹下包含了各章使用的预设模型和其他常用预设模型等。


