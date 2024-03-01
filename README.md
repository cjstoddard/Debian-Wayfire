# Debian-Wayfire
Wayfire does not work out of box on Debiam 12. For some reason wf-shell is no where to be found in the repo, so it muct be downlaoded and compiled from source. This should get you started with a basic working install of Wayfire. Please note, I al;ready hade meson and ninja installed on my machine, if you do not, you will need to install them and build-essential if you have not already done so.

sudo apt install alacritty gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk3-0.4 kanshi libcap-dev libdbusmenu-glib-dev libdbusmenu-gtk3-dev libglm-dev libgtkmm-3.0-dev libseat-dev libseat1 libvala-0.56-0 libvalacodegen-0.56-0 libwf-config-dev libwf-config1 libwf-utils-dev libwf-utils0 libwlroots-dev libwlroots10 libxcb-composite0-dev libxcb-dri3-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-present-dev libxcb-render-util0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb-xinput-dev mako-notifier slurp swaylock valac valac-0.56-vapi valac-bin wayfire wayfire-dev wdisplays wlogout wlr-randr wlsunset wofi xwayland

git clone [https://github.com/WayfireWM/wf-shell.git](https://github.com/WayfireWM/wf-shell.git￼cd)  
[cd](https://github.com/WayfireWM/wf-shell.git￼cd) wf-shell  
meson build --prefix=/usr --buildtype=release  
ninja -C build  
sudo ninja -C build install

curl <https://raw.githubusercontent.com/WayfireWM/wf-shell/master/wf-shell.ini.example> \~/.config/wf-shell.ini

cd ..

mkdir .config/wayfire  
cp /usr/share/doc/wayfire/examples/wayfire.ini .config/wayfire/wayfire.ini

sed -i '/# panel = wf-panel/c\\\\panel = wf-panel' .config/wayfire/wayfire.ini

sed -i '/# dock = wf-dock/c\\\\dock = wf-dock' .config/wayfire/wayfire.ini

mkdir -p \~/.config/wofi

> cat > .config/wofi/config << EOF    
> window {    
>   color: #A9B1BD;    
>   background-color: #2D3037;    
>   }  
>   #inner-box {    
>   margin: 5px;    
>   border: 2px solid #2D3037;    
>   background-color: #2D3037;    
> }  
> EOF
