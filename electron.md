https://www.christianengvall.se/electron-packager-tutorial/

npm install electron-installer-dmg --save-dev
npm install --save-dev electron-winstaller

"scripts": {
     "package-mac": "electron-packager . --overwrite --asar=true --platform=darwin --arch=x64 --icon=assets/icons/mac/icon.icns --prune=true --out=release-builds",
     "package-win": "electron-packager . --overwrite --asar=true --platform=win32 --arch=ia32 --icon=assets/icons/windows/icon.ico --prune=true --out=release-builds --version-string.CompanyName='CE' --version-string.FileDescription='CE' --version-string.ProductName='ElectronTutorialApp'",
     "package-linux": "electron-packager . --overwrite --asar=true --platform=linux --arch=x64 --icon=assets/icons/png/1024x1024.png --prune=true --out=release-builds",
     "create-installer-mac": "electron-installer-dmg ./release-builds/app.app electron-tutorial-app --out=release-builds --overwrite --icon=assets/icons/mac/icon.icns",
     "create-installer-win": "node installers/windows/createinstaller.js"
 }
 
electron-packager打包应用：
    MAC:--icon=./img/1.icns
    Windowns:--icon=./img/1.ico
    Linux:--icon=./img/1.ico
