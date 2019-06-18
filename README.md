# pyinstaller-in-pyzbar

#該程序需要兩個dll才能運行，在python環境目錄/Lib/site-packages/pyzbar/libiconv.dll 和 libzbar-64.dll

#將使用到的PIL和pyzbar 包拷貝到main.py同級目錄。 命令行cd到main.py目錄

#會在同級目錄下生成dist和build目錄，dist中會生成main.exe 但需要把libiconv.dll和libzbar-64.dll放到同級目錄才能運行 同時生成mina.spec文件 ，等會#用於將dll打包到exe中 $ pyinstaller.exe -F main.py -w -p pyzbar -p PIL 修改上面生成的main.spec文件，將兩個dll拷貝到當前目錄並修改binaries#部分內容

a = Analysis(['main.py'], 
pathex=['pyzbar', 'PIL', 'G:\code\QRCodeScaner\src'], 
binaries=[('libiconv.dll','./'),('libzbar-64.dll','./')], 
datas=[], 
hiddenimports=[], 
hookspath=[], 
runtime_hooks=[], 
excludes=[], 
win_no_prefer_redirects=False, 
win_private_assemblies=False, 
cipher=block_cipher, noarchive=False)

#命令行重新打包 pyinstaller.exe -F main.spec -p pyzbar -p PIL

#此時生成的main.exe 就可以單獨運行不用dll了
