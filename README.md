Yii1-ueditor-ext
===================
项目更名为Yii1-ueditor-ext，采用2推荐的方式重新命名，方便管理。

Yii v1.x 的UEditor扩展，支持的UEditor版本为1.4.3。

测试使用的PHP版本为5.5.9。

支持自动的缩略图管理。

支持水印。

使用TP框架的tpImage来生成和处理图片。

配置说明
---------------------

1、将ueditor放在项目的/protected/extensions/目录下。

2、在config.php中配置controllerMap，来指定ueditor的访问路径

```php
    'controllerMap'=>array(
        'ueditor'=>array(
            'class'=>'ext.ueditor.UeditorController',
        ),
    ),
```

可选配置:

```php
    'controllerMap'=>array(
        'ueditor'=>array(
            'class'=>'ext.ueditor.UeditorController',
            'config'=>array(),//参考config.json的配置，此处的配置具备最高优先级
            'thumbnail'=>true,//是否开启缩略图
            'watermark'=>'',//水印图片的地址，使用相对路径
            'locate'=>9,//水印位置，1-9，默认为9在右下角
        ),
    ),
```
3、在view中使用widget。

在原有的view中添加即可，注意id填写为原有的textarea的id。

注意，使用这个widget时，不要删除原有的代码，只要添加此处的代码即可。

```php
    $this->widget('ext.ueditor.UeditorWidget',
            array(
                    'id'=>'Post_content',//页面中输入框（或其他初始化容器）的ID
                    'name'=>'editor',//指定ueditor实例的名称,个页面有多个ueditor实例时使用
            )
    );
```
4、错误排除

- 出现错误首先应该打开调试工具查看请求返回具体信息。

- 出现错误请查看上传目录的权限问题。

- 扩展默认情况下需要登录权限才能上传文件。

- 默认上传到「应用」根目录（不是网站根目录）的upload/目录。

- 不要开启Yii的调试，因为UEditor的返回都是json格式，开启调试会导致返回格式不识别。

- 出现404错误可能是因为没有配置controllerMap。


其他说明
---------------------
1、1.4.3版本插件

参考地址：http://www.crazydb.com/archive/UEditor1.4.3-for-Yii1-扩展

2、原1.3.6版本插件

因为1.3.6版本作为一个比较稳定的版本，还是具备一定的使用价值（支持IE6/7，1.4.3以上版本将不再承诺支持IE6/7），因此保留下载地址。

下载地址：http://www.crazydb.com/upload/file/20140531/7384_yii-ext-ueditor136.tar.gz

参考：http://www.crazydb.com/archive/百度编辑器UEditor的Yii扩展