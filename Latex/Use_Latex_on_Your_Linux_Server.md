
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

Search `LaTeX Workshop` on your code-server and install it

![](https://pic3.zhimg.com/80/v2-37df048ea711ccd6191a06763899d952_1440w.webp)


### config your LaTeX Workshop

`Ctrl + Shift + p` and enter `setj`, select `Open User Settings JSON`

the path may be `/Your_Home/.local/share/code-server/User/settings.json`


































