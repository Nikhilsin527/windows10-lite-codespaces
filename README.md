# Tiny10 Lite Codespaces — dockur/windows

यह public repository [dockur/windows](https://github.com/dockur/windows) के supported `VERSION: "tiny10"` profile पर आधारित है।

## क्या सेट किया गया है

- Tiny10 automatic install: `VERSION: "tiny10"`
- 3 GB guest RAM
- 2 virtual CPU cores
- 20 GB qcow2 disk
- 1024×600 browser display
- Lossy web-VNC compression enabled
- Audio disabled
- Samba/shared-folder integration disabled
- KVM disabled ताकि GitHub Codespaces में start होने की संभावना रहे
- Web desktop port: **8006**

Tiny10 image इस repository में store नहीं है; upstream container installation के दौरान उसे download करता है।

## Start करने का तरीका

1. [Create Tiny10 Codespace](https://codespaces.new/Nikhilsin527/windows10-lite-codespaces) खोलें।
2. यदि विकल्प मिले तो **4-core machine** चुनें।
3. Codespace create करें और पहली installation पूरी होने दें।
4. **Ports → 8006 → Open in Browser** पर क्लिक करें।

पहली installation में download और VM setup के कारण काफी समय लग सकता है। Installation के दौरान Codespace बंद न करें।

## Login

```text
Username: TinyUser
Password: ChangeThisPassword
```

पहली बार login के बाद password तुरंत बदल दें। Password बदलने के लिए Codespace बनाने से पहले `.devcontainer/docker-compose.yml` में `PASSWORD` value edit करें।

## जरूरी performance limitation

GitHub Codespaces आम तौर पर `/dev/kvm` उपलब्ध नहीं कराता। इसलिए यह configuration `KVM: "N"` के साथ QEMU software emulation चलाती है। यह previous regular Windows 10 profile से हल्का होना चाहिए, लेकिन **Codespaces पर smooth performance की guarantee नहीं है**। अगर Tiny10 भी hang करे, तो मुख्य कारण hardware virtualization की कमी है।

वास्तव में smooth Tiny10 के लिए KVM-enabled Linux VM/VPS चाहिए।

Windows activation/licensing इसमें शामिल नहीं है; valid license का उपयोग करें।

## Quota warning

Tiny10 VM Codespaces storage और compute quota इस्तेमाल करेगा। काम पूरा होने पर Codespace stop या delete कर दें।
