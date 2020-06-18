# pygame开发实例

> 注意pygame默认加载位图

## 开发环境
1. pygame for mac
    ```
    $ brew install hg sdl sdl_image sdl_ttf
    $ brew install sdl_mixer portmidi        //pygame包含声音的库
    $ pip3 install pygame
    ```

## .gitignore
    ```python
    # misc
    .DS_Store

    # idea
    .idea

    # git ignore
    .gitignore

    # venv
    /venv
    ```

## 开发思路
### 文件结构
> 在原先思路上稍作改变
```
`-- .
    |-- src
    |   |-- components
    |   |   |-- button.py
    |   |   `-- scoreboard.py
    |   |-- core
    |   |   |-- game_functions.py
    |   |   `-- game_stats.py
    |   |-- models
    |   |   |-- alien.py
    |   |   |-- bullet.py
    |   |   `-- ship.py
    |   |-- aliens_invasion.py
    |   `-- settings.py
    `-- static
        `-- imgs
            |-- alien.bmp
            `-- ship.bmp
```
- components: 组件，游戏界面的组件
- core: 核心功能，比如游戏进行刷新的函数
- models: 模型，设计的游戏中的模型
- static/imgs: 储存需要的图片

这样做的目的是更好的区分各个python模块，如果项目变大方便查找文件。

### 项目实现过程
1. 显示模型
2. 控制模型移动
3. 锦上添花——记分板、开始按钮等

总之就是先实现基本功能，后添加新的功能。\
这个实现的过程与java画板类似，在此不多赘述
