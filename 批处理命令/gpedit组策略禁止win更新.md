gpedit组策略禁止win更新



    @echo off
    
    pushd "%~dp0"
    
    dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt
    
    dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt
    
    for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"C:\Windows\servicing\Packages\%%i"
    
    pauses
    
> 存储以上代码为.bat后缀的文件，名字随便起并以管理员身份运行就可以了