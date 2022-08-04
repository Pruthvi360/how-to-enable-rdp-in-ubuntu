# how-to-enable-rdp-in-ubuntu

LOGIN INTO THE VM AND BECOME ROOT 
command: sudo su
command: apt update && upgrade
command: apt install xrdp -y
command: nano /etc/xrdp/xrdp.ini
Edit inside it: encrypt_level=high
command: ufw allow 3389/tcp
command: nano /etc/polkit-1/localauthority.conf.d/02-allow-colord.conf
Paste inside it: polkit.addRule(function(action, subject) {
if ((action.id == “org.freedesktop.color-manager.create-device” || action.id == “org.freedesktop.color-manager.create-profile” || action.id == “org.freedesktop.color-manager.delete-device” || action.id == “org.freedesktop.color-manager.delete-profile” || action.id == “org.freedesktop.color-manager.modify-device” || action.id == “org.freedesktop.color-manager.modify-profile”) && subject.isInGroup(“{group}”))
{
return polkit.Result.YES;
}
});

command: /etc/init.d/xrdp restart
