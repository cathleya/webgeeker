#  Sidebar Theme


> https://gist.github.com/renz45/1854721


[Default.sublime-theme](Default.sublime-theme)


## Default.sublime-theme
> This re-styles your sublime text 2 sidebar to be darker, so it doesn't blind you when using a dark theme.  
> Save the Default.sublime-theme file into packages/user  

```code

[
    {
        "class": "close_button",
        "layer0.texture": "Theme - Default/light_x_bright.png",
        "layer0.opacity": 0.7
    },
    {
        "class": "sidebar_tree",
        "layer0.tint": [50, 50, 50] //230,230,230
    },
    {
        "class": "sidebar_heading",
        "color": [200, 200, 200],  //130,130,130 headers (open files, folders)
        "shadow_color": [0, 0, 0]// 250 250 250
    },
    {
        "class": "sidebar_label",
        "color": [200, 200, 200]// 0 0 0  text in the sidebar tree
    },
    {
        "class": "text_line_control",
        "layer0.tint": 0
    },
    {
        "class": "quick_panel_row",
        "layer0.texture": "Theme - Default/panel_row.png",
        "layer0.inner_margin": [2, 2, 2, 2],
        "layer0.opacity": 1.0
    },
    {
        "class": "quick_panel_row",
        "attributes": ["selected"],
        "layer0.texture": "Theme - Default/panel_row_selected.png"
    },
    {
        "class": "quick_panel_label",
        "bg": [87, 87, 87, 255],
        "selected_match_fg": [255, 255, 255, 255],
        "selected_bg": [64, 64, 64, 255]
    },
    {
        "class": "quick_panel_path_label",
        "bg": [87, 87, 87, 255],
        "selected_match_fg": [255, 255, 255, 255],
        "selected_bg": [64, 64, 64, 255]
    },
    {
        "class": "quick_panel_score_label",
        "bg": [87, 87, 87, 255],
        "selected_fg": [166, 229, 255, 255],
        "selected_bg": [64, 64, 64, 255]
    },
    {
        "class": "auto_complete_label",
        "bg": [255, 255, 255, 255],
        "selected_match_fg": [0, 0, 0, 255],
        "selected_bg": [156, 185, 223, 255]
    },
    {
        "class": "fold_button_control",
        "layer1.texture": "Theme - Default.arrow_right.png"
    }
]
``` 



https://zhuanlan.zhihu.com/p/23826777
https://github.com/xgqfrms-GitHub/webgeeker/tree/gh-pages/tools


