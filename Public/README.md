﻿#### 文件目录
* +assets - lib 文件     <br/>
  &emsp; +css           <br/>
  &emsp; +fonts         <br/>
  &emsp; +js            <br/>
  &emsp; +layer         <br/>
  
* +css - sass 编译目录   <br/>
  &emsp; +icons         <br/>
  &emsp; -base.css      <br/>

* -img - 图片文件

* +js - js 逻辑代码      <br/>
  &emsp; +models - es5逻辑目录,es6编译后的目录    <br/>
  &emsp; +models-es6 - es6逻辑目录               <br/>
  &emsp; +public                                <br/>
  &emsp; -controller.js                         <br/>
  &emsp; -main.js - 程序主入口                   <br/>
  
* +sass - sass 开发目录

#### install
*   npm install --save-dev / npm install --global
*   bower install

#### run task
*   gulp framework

*   gulp sass

*   gulp

*   gulp spriteSmith

        1.  gulp.spritesmith 生成雪碧图
        
        2.  return gulp.src('./sass/icons/*.png') //需要合并的图片地址
            .pipe(spritesmith({
                imgName: 'icons/sprite.png',
                cssName: 'sprite.css',
                padding: 5,
                algorithm: 'binary-tree',
                cssTemplate: "./sass/icons/spriteTemplate.css"
            }))
            .pipe(gulp.dest('./css')); //相对路径
        
        3.  参数:
            'imgName' : 保存合并后对于 `css目录` 的图片地址
            'cssName' : 保存合并后对于 `css目录` 的样式地址
            'padding' : 合并时两个图片的间距
            'algorithm' : 图片合成分布。可选,分别为【'top-down'、'left-right'、'diagonal'、'alt-diagonal'、'binary-tree'】
            'cssTemplate' : 生成css的模板文件。 字符串(模板地址文件)、函数。
                模板格式如下：
                    `css`
                    /** spriteTemplate.css start **/
                        {{#sprites}}
                        .icon-{{name}}{
                            background-image: url("{{escaped_image}}");
                            background-position: {{px.offset_x}} {{px.offset_y}};
                            width: {{px.width}};
                            height: {{px.height}};
                        }
                        {{/sprites}}
                    /** spriteTemplate.css end **/  
                函数样式格式如下:
                    `function`
                    /** function start **/
                        cssTemplate: function (data) {
                            var arr = [];
                            data.sprites.forEach(function (sprite) {
                                arr.push(".icon-" + sprite.name +
                                "{" +
                                "background-image: url('" + sprite.escaped_image + "');" +
                                "background-position: " + sprite.px.offset_x + "px " + sprite.px.offset_y + "px;" +
                                "width: " + sprite.px.width + ";" +
                                "height: " + sprite.px.height + ";" +
                                "}\n");
                            });
                            return arr.join("");
                        }                        
                    /** function end **/
            
#### run server
*   node server