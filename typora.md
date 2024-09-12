### 左侧目录，右侧大纲显示

```
/* 其他主题代码 */

:root {
    --my-sidebar-header-height: 40px;
}

/* 增加右侧侧边栏显示大纲 */
/*=============================== start ========================================*/
/* 切换 文件/大纲 按钮 隐藏 */
#typora-sidebar .sidebar-tab-btn,
#typora-sidebar:hover .sidebar-tab-btn {
   opacity: 0; 
   z-index: -10px;
}


/* 内容部分，留出右边的宽度 */
.pin-outline content {
    right: var(--sidebar-width);
    border-right: 1px solid rgba(0,0,0,.07);
}

/* 将 大纲 移动到右边 */
.pin-outline .active-tab-files #outline-content {
    display: block!important;
    position: fixed;
    top: 40px;
    right: 0;
    left: calc(100% - var(--sidebar-width));

    width: var(--sidebar-width);
    max-width: var(--sidebar-width);
    min-width: 100px;
    
    height: calc(100% - var(--my-sidebar-header-height));
    padding-left: 8px;
}

/* 显示大纲标题 */
#sidepanel-segmented-input-outline {
    display: block!important;
    position: fixed;
    top: 0;
    right: 0;
    left: calc(100% - var(--sidebar-width));

    height: var(--my-sidebar-header-height);
    width: var(--sidebar-width);
}

/*================================  end =======================================*/

/* 其他主题代码 */
```

