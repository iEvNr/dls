@echo off 
echo %~dp0
cd /d %~dp0

SETLOCAL EnableExtensions DisableDelayedExpansion
for /F %%a in ('echo prompt $E ^| cmd') do (
  set "ESC=%%a"
)
SETLOCAL EnableDelayedExpansion

:WAITLOOP1
echo ========================================================================
echo !ESC![32mTrying to inject...!!ESC![0m
echo ========================================================================

timeout 5

echo ========================================================================
echo !ESC![32mTrying d3d11!!ESC![0m
echo ========================================================================

timeout 3

modmap.exe ModernWarfare.exe d3d11.dll sys32.dll
if "%ERRORLEVEL%"=="0" goto DONE


goto WAITLOOP2


:WAITLOOP2
echo ========================================================================
echo !ESC![31mFailed d3dll going to d3d12!ESC![0m
echo ========================================================================

timeout 3

echo ========================================================================
echo !ESC![32mTrying d3d12!!ESC![0m
echo ========================================================================

modmap.exe ModernWarfare.exe d3d12.dll sys32.dll
if "%ERRORLEVEL%"=="0" goto DONE



goto WAITLOOP3


:WAITLOOP3
echo ========================================================================
echo !ESC![31mFailed d3dl2 going to ntd11!ESC![0m
echo ========================================================================

timeout 3
echo ========================================================================
echo !ESC![32mTrying ntd11!!ESC![0m
echo ========================================================================

modmap.exe ModernWarfare.exe ntdll.dll sys32.dll
if "%ERRORLEVEL%"=="0" goto DONE

goto WAITLOOP4

:WAITLOOP4
echo ========================================================================
echo !ESC![31mFailed ntd11 going to discord_game_sdk.dll!ESC![0m
echo ========================================================================
modmap.exe ModernWarfare.exe discord_game_sdk.dll sys32.dll
if "%ERRORLEVEL%"=="0" goto DONE

echo ========================================================================
echo !ESC![31mFAILED d3d11, d3d12, ntd11, discord_game_sdk!ESC![0m
echo ========================================================================


:DONE
echo ========================================================================
echo !ESC![32mINJECTED!!ESC![0m
echo ========================================================================
pause...
