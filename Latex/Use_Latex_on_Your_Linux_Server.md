
# How to Use Latex on Your Linux Server without Root Permission

## Install TexLive

just copy

```{sh}
cp -r /home/xumeng/app/texlive /your_path/

# your path may be  /home/xumeng/.local/
```

then

add the following text to your ~/.bashrc or ~/.bash_profile, source it.
```{sh}
export PATH=/your_path/texlive/bin/x86_64-linux:$PATH    
export INFOPATH=$INFOPATH:/your_path/texlive/texmf-dist/doc/info
export MANPATH=$MANPATH:/your_path/texlive/texmf-dist/doc/man
```
finally, test!

```{sh}
tex -v

latex -v
```


## Install Code Server and LaTeX Workshop Extension

## Install code-server

ref: [install code server by conda](https://github.com/sdy2813/bioprogram/blob/main/Linux/code-server.md)

run code-server like this

```{sh}
export PATH="/your_path/texlive/bin/x86_64-linux:/usr/bin:$PATH"
code-server
```



### install LaTeX Workshop


Search `LaTeX Workshop` on your code-server and install it

![](https://pic3.zhimg.com/80/v2-37df048ea711ccd6191a06763899d952_1440w.webp)


### config your LaTeX Workshop

`Ctrl + Shift + p` and enter `setj`, select `Open User Settings JSON`

the path may be `/Your_Home/.local/share/code-server/User/settings.json`

you can just copy the follow code to yours. notice, change `/home/xumeng/app/texlive`!

```{json}
{
    "latex-workshop.latex.tools": [
        {
            "name": "latexmk-xelatex",
            "command": "/home/xumeng/app/texlive/bin/x86_64-linux/latexmk",
            "args": [
                "-xelatex",
                // "-f",
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                // "-pdf",
                "%DOCFILE%"
            ],
            "env": {
                "PATH": "/home/xumeng/app/texlive/bin/x86_64-linux:/usr/bin"
            }
        },
        {
            "name": "xelatex",
            "command": "/home/xumeng/app/texlive/bin/x86_64-linux/xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "latexmk (xelatex)",
            "tools": [
                "latexmk-xelatex"
            ]
        },
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ]
        },
    ],
    "files.autoSave": "onFocusChange",
    "[latex]": {
        "editor.defaultFormatter": "James-Yu.latex-workshop"
    },
    "latex-workshop.latex.autoClean.run": "onFailed",
    "latex-workshop.latex.autoBuild.run": "onSave",
    "git.ignoreLegacyWarning": true,
    "editor.wordWrap": "on",
    "editor.fontSize": 16,
    "svg.preview.mode": "svg",
    "editor.formatOnSave": true,
}
```

## Install Windows Fonts on Your Accounts

just copy my file to your path

```{sh}
cp -r /home/xumeng/.local/share/fonts /your_home/.local/share/
```

fresh your fonts

```{sh}
fc-cache -f -v
fc-list | grep "Arial"
```

Now, you'd use Chinese Words on Latex.

## Reference

1. ![linux no root 安装arial字体](https://www.jianshu.com/p/b54f62b8ca29)
1. ![Visual Studio Code (vscode)配置LaTeX](https://zhuanlan.zhihu.com/p/166523064)
1. ![如何在不使用root权限下安装Latex ](http://xuzhougeng.com/archives/install-latex-without-root)

















