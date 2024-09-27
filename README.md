## helix editor配置文件路径
~/.config/helix/

## 宜配合tmux使用
1. 启动:tmux
2. 退出:exit 或 Ctrl+d 或批量关闭使用tmux kill-session -t 0
3. 分屏(上下):Ctrl+b,"
4. 切换分屏:Ctrl+b,;

## 其它
1. apt install clangd lldb tmux
2. cd /usr/bin;ln -s lldb-vscode-14 lldb-dap

## rust env and helix's install from source
```
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
. "$HOME/.cargo/env"
rustc --version
https://mirrors.ustc.edu.cn/help/crates.io-index.html #for crates.io faster
# apt install helix (if not useful)
git clone https://github.com/helix-editor/helix
cd helix
cargo install --path helix-term --locked # try again for error link to github
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
