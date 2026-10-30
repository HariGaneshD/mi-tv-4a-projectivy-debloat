# mi-tv-4a-projectivy-debloat
Clean up your Xiaomi Mi TV 4A with ADB. Disable PatchWall, ads, analytics, Google TV recommendations, and Live TV components. Install and configure Projectivy Launcher as the default home screen with simple restore scripts to revert changes anytime.
<img width="2974" height="2268" alt="image" src="https://github.com/user-attachments/assets/a1676cc7-c0fa-47e4-932d-c232f3264cf8" />
disable_ads.ps1

adb shell pm disable-user --user 0 com.google.android.tvrecommendations
adb shell pm disable-user --user 0 com.google.android.leanbacklauncher.recommendations
adb shell pm disable-user --user 0 com.google.android.backdrop
adb shell pm disable-user --user 0 com.google.android.apps.mediashell
adb shell pm disable-user --user 0 com.miui.tv.analytics
adb shell pm disable-user --user 0 com.xiaomi.statistic
projectivy_setup.ps1

adb shell cmd package set-home-activity com.spocky.projengmenu/com.spocky.projengmenu.ui.home.MainActivity
adb shell pm disable-user --user 0 com.google.android.tvlauncher
adb shell pm disable-user --user 0 com.google.android.leanbacklauncher
adb shell pm disable-user --user 0 com.mitv.tvhome.atv
adb reboot

Disable Live TV
adb shell pm enable com.google.android.tvlauncher
adb shell pm enable com.google.android.leanbacklauncher
adb shell pm enable com.mitv.tvhome.atv
adb shell cmd package set-home-activity com.google.android.tvlauncher/.MainActivity
mkdir mi-tv-4a-projectivy-debloat
cd mi-tv-4a-projectivy-debloat

git init
git add .
git commit -m "Initial commit"

git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mi-tv-4a-projectivy-debloat.git
git push -u origin main
