# CSDN-Clean-Print-PDF

使用方法：F12打开检查，选择console控制台，粘贴代码
<img width="1440" alt="截屏2024-11-01 12 24 21" src="https://github.com/user-attachments/assets/08e39cd8-569d-4120-b9ab-3940a55f3e9d">

 <img width="1440" alt="截屏2024-11-01 12 23 23" src="https://github.com/user-attachments/assets/e69b9561-b13d-45b1-95db-30e114d0cc0d">

 
**Description**:  
This repository provides a JavaScript snippet for a cleaner and well-formatted PDF printing experience on CSDN blog pages. It removes unnecessary elements such as ads, sidebars, and comment sections, adjusts page layout, and ensures long lines in code blocks wrap correctly when printed, preventing text cut-off issues in the generated PDF.
 
此仓库提供了一个 JavaScript 代码段，帮助在 CSDN 博客页面上获得更简洁且格式良好的 PDF 打印体验。代码会移除广告、侧边栏和评论区等不必要的元素，调整页面布局，并确保代码块中的长行在打印时正确换行，避免生成的 PDF 中文本被截断的问题。

---

**Features**:  
1. Automatically removes ads, comments, and sidebars from CSDN pages for a cleaner view.
2. Adjusts the layout to fit the page width, making it suitable for PDF conversion.
3. Ensures code blocks are fully visible without line cut-offs in the final PDF. 
1. 自动从 CSDN 页面移除广告、评论和侧边栏等元素，使页面更加简洁。
2. 调整布局以适应页面宽度，适合转换为 PDF。
3. 确保代码块完全可见，在最终的 PDF 中不会出现行被截断的问题。 

**Usage**:  
Simply copy the JavaScript snippet and paste it into the browser console when on a CSDN blog page, or set it up as a bookmarklet for quicker access.
只需复制 JavaScript 代码段，并在 CSDN 博客页面上将其粘贴到浏览器控制台中，或将其设置为书签快捷访问。

 

```javascript
(function(){
    $("#side").remove();
    $("#comment_title, #comment_list, #comment_bar, #comment_form, .announce, #ad_cen, #ad_bot").remove();
    $(".nav_top_2011, #header, #navigator").remove();
    $(".p4course_target, .comment-box, .recommend-box, #csdn-toolbar, #tool-box").remove();
    $("aside").remove();
    $(".tool-box").remove();
    $("main").css('display','content'); 
    $("main").css('float','left'); 

    $(".toolbox-list, .profile-img, .isdefault, .profile-name, .left-toolbox").remove();
    $("#is-like-img").remove();

    // 自动展开所有代码块
    $(".set-code-hide").removeClass("set-code-hide");

    // 添加打印样式
    var style = document.createElement('style');
    style.innerHTML = `
        @media print {
            /* 将页面内容适应页面宽度 */
            body, main {
                width: 90%;
                max-width: 90%;
                overflow: visible;
                word-wrap: break-word; /* 强制长单词换行 */
                white-space: normal;    /* 设置正常换行 */
            }
            pre, code {
                white-space: pre-wrap; /* 保持预格式化文本换行 */
                word-break: break-all; /* 长文本在单词内断行 */
                overflow-wrap: break-word;
            }
        }
    `;
    document.head.appendChild(style);

    window.print();
})();
```
 
 
 
