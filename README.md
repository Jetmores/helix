## helix editor配置文件路径
~/.config/helix/

## 宜配合tmux使用
1. 启动:tmux
2. 退出:exit 或 Ctrl+d 或批量关闭使用tmux kill-session -t 0
3. 分屏(上下):Ctrl+b,"
4. 切换分屏:Ctrl+b,;

## 其它
1. apt install clangd lldb tmux xclip #xclip work with helix(wsl ok|aly no)
2. cd /usr/bin;ln -s lldb-vscode-14 lldb-dap

## rust env and helix's install from source
```
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
. "$HOME/.cargo/env"
rustc --version
https://mirrors.ustc.edu.cn/help/crates.io-index.html #for crates.io faster
echo 'export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup' >> .bashrc # need test
# apt install helix
sudo apt install software-properties-common
sudo add-apt-repository ppa:maveonair/helix-editor
sudo apt update
sudo apt install helix
# source
git clone https://github.com/helix-editor/helix
cd helix
# try again for error link to github build tree-site or HELIX_DISABLE_AUTO_GRAMMAR_BUILD=1 cargo install --path helix-term --locked
cargo install --path helix-term --locked 
cp -r runtime/ ~/.config/helix # or just onestep: git clone https://gitlab.com/lets2rs/helix.git
```

## zig env
```
curl -LOk https://ziglang.org/download/0.13.0/zig-linux-x86_64-0.13.0.tar.xz
tar -Jxvf zig-linux-x86_64-0.13.0.tar.xz
mv zig-linux-x86_64-0.13.0 .zig
echo 'export PATH="$HOME/.zig:$PATH"' >> .bashrc
zig version
# zls build
git clone https://github.com/zigtools/zls
cd zls
zig build -Doptimize=ReleaseSafe #error: /root/.zig/zig-linux-x86_64-0.14.0-dev.1671+085cc54aa/zig build -Doptimize=ReleaseSafe
cp zig-out/bin/zls /usr/local/bin/
hx --health zig
```

## programming
### 静态库和动态库的生成和调用(一样)
```
g++ -c example.cc && ar rcs libexample.a example.o
g++ -fPIC -shared -o libexample.so example.cc 
ldd ./app
echo 'export LD_LIBRARY_PATH=/mypath/:$LD_LIBRARY_PATH' >>.bashrc ; . ~/.bashrc
或者sudo echo 'mypath/' >> /etc/ld.so.conf; sudo ldconfig //重建/etc/ld.so.cache
```
### gdb设定disas的intel模式
```
sudo echo 'set disassembly-flavor intel' >>/etc/gdb/gdbinit
```
