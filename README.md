# navicat_win


Navicat off

Win + R, enter regedit, enter

Delete HKEY_CURRENT_USER\Software\PremiumSoft\Data

Expand HKEY_CURRENT_USER\Software\Classes\CLSID

Expand each subfolder. If it contains only one folder named Info, delete it


``` bat
@echo off

echo Delete HKEY_CURRENT_USER\Software\PremiumSoft\NavicatPremium\Registration15XEN
echo waiting......
reg delete "HKEY_CURRENT_USER\Software\PremiumSoft\NavicatPremium\Registration15XEN" /va /f
echo.

echo Delete Info folder under HKEY_CURRENT_USER\Software\Classes\CLSID
echo waiting......

for /f %%i in ('"REG QUERY "HKEY_CURRENT_USER\Software\Classes\CLSID" /s | findstr /E Info"') do (
    echo %%i
	reg delete %%i /va /f
	reg delete %%i /f
)

echo.
echo Finish

pause
```
