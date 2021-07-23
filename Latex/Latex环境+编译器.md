### Atom+texlive
### CTeX套装(WinEdit)
### CTex + TeXstudio  必须使用 编译器XeLaTex
### MikTex + TeXstudio


<font size = 4 color = 0xaabbcc>
</br></br>

- 中文没法显示</br>
1.在上方菜单栏options-configure TeXstudio-build。把Default compiler改成XeLaTeX。 
然后，在tex文件的代码中插入\usepackage{xeCJK} 
最后，点F5，即可看到中文成功显</br></br>
2.首先，在上方菜单栏options-configure TeXstudio-build。把Default compiler改成XeLaTeX。 
然后，在tex文件的代码中插入\usepackage{fontspec} 
\setmainfont[Mapping=tex-text]{KaiTi} 

</font>


