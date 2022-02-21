# Table of Contents
 
1. [Prerequisites](#prerequisites-and-stability-tests)
   1. [Overclocking Software](#overclocking-software)
   2. [Monitoring Software](#monitoring-software)
   3. [Benchmarks](#benchmarks)
      1. [Recommended](#recommended)
      2. [Avoid](#avoid)
2. [Overclocking Info](#overclocking-info)
   1. [What is overclocking and undervolting?](#what-is-overclocking-and-undervolting)
   2. [Benefits of Overclocking and Undervolting](#benefits-of-overclocking-and-undervolting)
   3. [Overclocking vs. Undervolting](#overclocking-vs-undervolting)
   4. [Misconceptions](#misconceptions)
4. [Overclocking](#overclocking)
   1. [Setup](#setup)
   2. [Finding a Core Clock](#finding-a-core-clock)
   3. [Finding a Memory Clock](#finding-a-memory-clock)
   4. [Undervolting](#undervolting)
5. [Flashing a VBIOS](#flashing-a-vbios)
   1. [VBIOS Information](#vbios-information)
   2. [How to Flash a VBIOS](#how-to-flash-a-vbios)
   3. [VBIOS Troubleshooting](#vbios-troubleshooting)
6. [Miscellaneous](#miscellaneous)
   1. [Fixing a boot loop](fixing-a-boot-loop)
   2. [NVCleanstall/DDU](#nvcleanstallddu)
7. [Tips and Tricks](tips-and-tricks)
   
# Prerequisites and Stability Tests
  ## Overclocking Software
   * [MSI Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards): This software is the most widely used and robust. Other software may be lacking in certain features and are generally not recommended.
  ## Monitoring Software
   * [HWiNFO](https://www.hwinfo.com/download/): HWiNFO is the most frequently used monitor software as it presents the values of all the sensors available and is a good software to have when overclocking your CPU, RAM, and GPU.
   * [GPU-Z](https://www.techpowerup.com/download/techpowerup-gpu-z/): GPU-Z is a software that will report the model, vbios, and version of your GPU.
   * [OCCT](https://www.ocbase.com/download): OCCT is a piece of software that stress tests while providing sensor values from HWiNFO. This can be used instead of HWiNFO while running an OCCT test.
  ## Benchmarks
  ### Recommended
   * One of the best stress tests is just playing games. There is currently no conclusive stress test for GPUs other than OCCT and playing games is a great way to find instability.
   * [Superposition](https://benchmark.unigine.com/superposition): This is a benchmark that will stress your GPU and VRAM well and is good at finding instability. It is used for getting reliable scores to see performance regressions. Make sure to set the [preset](https://cdn.discordapp.com/attachments/721078648911954103/916013522993942528/unknown.png) so it [maxes out the VRAM](https://cdn.discordapp.com/attachments/873056719822008381/873375349814206484/unknown.png) *[without going over](https://cdn.discordapp.com/attachments/873056719822008381/873380510393565224/unknown.png)*.
   ![image](https://user-images.githubusercontent.com/69487009/155036041-4eed7d4b-1103-4d88-876c-d5878cbaf70e.png)
   * [3DMark](https://store.steampowered.com/app/223850/3DMark/): This is widely used, to stress your GPU well, and is also good at finding instability. Note that it is not recommended for performance regressions as there is a lot of variance in scores and Superposition is better for getting accurate scores. There is a demo version you can download for free. Run the Time Spy benchmark as it is the most relevant test.
   * [OCCT](https://www.ocbase.com/): This test is the best for finding errors and stressing your GPU, however, it requires careful fine-tuning and takes a while to find the “sweet spot” as it power throttles at stock settings.
   ![image](https://user-images.githubusercontent.com/69487009/155036223-fe2aebc0-f60e-433f-81e6-325db9e3cfa8.png)
     * V10: Go to the [3D tab](https://cdn.discordapp.com/attachments/721078648911954103/916023019313438730/unknown.png) under [test](https://cdn.discordapp.com/attachments/721078648911954103/916023115128135721/unknown.png). Turn on [error detection](https://cdn.discordapp.com/attachments/721078648911954103/916023308510715914/unknown.png) and [shader complexity to 8](https://cdn.discordapp.com/attachments/721078648911954103/916023534663385168/unknown.png). Decrease [GPU usage limit (%)](https://cdn.discordapp.com/attachments/721078648911954103/916025031673393182/unknown.png) until you just barely (5% of the time) power throttle. Click start and leave it running for an hour.
     * V11: [Coming soon](https://www.youtube.com/watch?v=QvHyalfsJdY).
  ### Avoid
   * Furmark: Draws a lot of power and doesn't effectively test as power limiting will be prevalent and temperatures will be elevated.
   * Kombustor: Same issue as Furmark.
   * Heaven: This is a very old testing program (13 years ago) that doesn’t stress your GPU a lot. However, it can be useful because it can be run in the background and loops for free. This program is not recommended unless you want to run it in the background for extended periods. If you do decide to use this, your settings should look like this. ![image](https://user-images.githubusercontent.com/69487009/155033902-2cc5dc72-f71a-48f2-b3b4-5fe1c069b65d.png)
  
# Overclocking Info
 ## What is Overclocking and Undervolting?
  * Overclocking is the process of increasing clock speeds and performance for generally higher heat and lower stability. Undervolting is the process of limiting the amount of voltage supplied to the GPU and will lower wattage, voltage, and temperatures.
 ## Benefits of Overclocking and Undervolting
  * Overclocking can provide those extra frames or decrease the processing time in workloads and provide you with a slightly better experience. Undervolting will reduce temperatures and voltages and will provide you with a quiet and stable experience.
 ## Overclocking vs. Undervolting
  * Overclocking typically increases temperatures to gain performance. Undervolting will decrease temperatures and voltage to give consistent performance. While with overclocking, you may achieve a higher clock speed than undervolting, that clock speed may not be sustained under stress. They both have their place and you should choose the one that better fits your needs.
 ## Misconceptions
  * Overclocking is dangerous: Modern Nvidia GPUs are locked in terms of how far you can push the voltage unless you have a modded VBIOS or have a physical modification to your card. The voltage that your card will use is safe and increasing clock speeds will not increase the voltage to unsafe values.
  * Overclocking too much is bad: There is no such thing as overclocking a modern GPU with a hard voltage lock and a normal VBIOS too much. The only time where an overclock is “bad” is when it’s unstable and that is fixed by stability testing.
  * Undervolting will lower performance: Undervolting may not be optimal for every card. However, it will improve performance when power limited, and reduce temperatures otherwise (12.5 - 15 MHz increase for every 5°C cooler).
  * Core voltage adds more voltage: The core voltage slider will generally not do much but it increases the aggressiveness of the V/F curve and makes your GPU use the higher voltage points more but does not add more voltage.
  * Dragging the point at the correct voltage to your desired clock speed is a common way to undervolt. This is an [unoptimal way](https://www.youtube.com/watch?v=RH3FZXvBkiE) because of the [effective clock speed](https://cdn.discordapp.com/attachments/714879622181028032/874460000565739550/unknown.png) being lower than the [clock speed displayed](https://cdn.discordapp.com/attachments/714879622181028032/945465118664323092/unknown.png) when using this method. Instead, use the slider in Afterburner to change clock speeds.

# Overclocking
 ## Setup
  1. Download [MSI Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards) and set a [fan curve](https://media.discordapp.net/attachments/873056719822008381/873068974546509855/fanc.png). Settings -> Fan -> Enable User Defined Control.
  2. While still in settings, go to User Interface -> User interface skinning properties and select a skin such as the MSI Cyborg Afterburner skin as it will be easier to follow.
  3. Download [HWiNFO](https://www.hwinfo.com/download/) and run it in [sensors only](https://cdn.discordapp.com/attachments/721078648911954103/945177008671952906/unknown.png).
  4. Go to MSI Afterburner, [max out power and temp limits](https://cdn.discordapp.com/attachments/873056719822008381/873365104442351626/unknown.png), and put the priority on the power limit. Note that laptops and some GPUs will not be able to go over 100%. This can be fixed by shunting or a different VBIOS
 ## Finding a Core Clock
  * Open Afterburner and raise the core clock speed using the slider in increments of 15 MHz for Turing/Ampere (30/20/16 series) or 12.5 MHz for Pascal (10 series). You will be limited by temperatures (always), and your card's power limit. There is no "limit" on how far you can overclock, however, you will know you reached the limit once you experience errors or crashes in stress tests and games. Keep in mind that an overclock can be stable in one game but not another. 
  * Apply the settings ![image](https://user-images.githubusercontent.com/69487009/155014073-4aac5d7b-91d6-4b96-abd1-ab51287cb248.png) and save ![image](https://user-images.githubusercontent.com/69487009/155004968-6f7ee82e-1575-4605-9932-644e5d702d45.png)
them to a profile. ![image](https://user-images.githubusercontent.com/69487009/155006086-5e300602-f099-4c6e-a3bf-29962b2905d2.png)
  * Click this ![image](https://user-images.githubusercontent.com/69487009/155013987-f6c7f084-c4cb-4804-bc98-1786056959a7.png) to have the overclock applied at startup.
  * Test the overclock, see if it is stable in both benchmarks and games, and monitor the temperatures using HWiNFO and stay under 80°C on the core and 95°C for hotspot.
  * If stable, increase core clock speeds in increments of +15 MHz/12.5 MHz using the slider or by typing in a value. If the benchmarks or games crash, decrease clock speeds by the same amount and retest until you have reached stability.
  ## Finding a Memory Clock
  * After you have tested the overclock sufficiently and confirmed its stability, you can start increasing the [memory clock](https://cdn.discordapp.com/attachments/721078648911954103/912854031293120583/unknown.png). Start at a memory clock of 500 MHz and increase in increments of 50-100 MHz. Note that memory clocks will usually scale much higher than core clocks (even over 1000 MHz).
  * To test the stability of the memory clock, you will need to look for performance regressions and artifacts. If you see any regression or lowering in score or any visual [artifacts](https://cdn.discordapp.com/attachments/721078648911954103/912854281768562708/IysjurtuAhMsoW2Z0iHIPusanO2CxdTIbLpRYcezRcTPzONeW3ImUcHcBiWJDvY-vKYsHaB5OTXQdJjvmjvWSHG2BOBRvz2Pp84K1DwTqQA.png), decrease the memory clock by 50-100 MHz and retest. The recommended benchmark for finding performance regressions (GDDR6X) is [Unigine Superposition](https://benchmark.unigine.com/superposition) as the scores are consistent.
  ![image](https://user-images.githubusercontent.com/69487009/155003914-986b3fbb-6f76-4f8a-b4c5-0d5351b7d2f6.png)
  * Test the overclock, see if it is stable in both benchmarks and games, and monitor the temperatures using HWiNFO and stay under 80°C on the core and 95°C for hotspot.
  * If stable, increase memory clock by 50-100 MHz and if unstable, decrease memory clock in increments of 50-100 MHz and retest. Continue repeating this process until you have found your maximum stable overclock.
 ## Undervolting
  * Click CTRL F to open the curve editor and [this](https://www.youtube.com/watch?v=LPpW9yXHvOU) guide and start at a baseline of 900 mV.
  * Select all the points past the voltage you want (900 mV) by holding down shift and left click and highlighting.
  * Drag all the points down by selecting a point and dragging it down.
  * Click apply ![image](https://user-images.githubusercontent.com/69487009/155014083-1b40ab17-e804-42fc-b524-94d7eba65dc1.png) to apply the undervolt and voltage curve you set.
  * Run a variety of workloads and games and check HWiNFO for power throttling ![image](https://user-images.githubusercontent.com/69487009/155013749-0e22d23b-4d01-4e3a-b253-374171d38ae2.png) in HWiNFO under GPU Performance Limiters.
  * If you are power throttling in-game, lower voltage by 25 mV, and retest. Once you are satisfied with temperatures and are not power throttling, you have found the optimum voltage.

# Flashing a VBIOS
 This section is for people who have already tested their overclocks but still want that additional headroom. Flashing a VBIOS can be very helpful as it can increase power limits which can increase overclocking headroom. It can also be risky and can void the warranty.
 ## VBIOS Information
  * Ensure that the card of the new VBIOS you’re flashing from has the same power connectors as the card you’re flashing to (2x8 pin, 1x12 pin, etc).
  * Check the number of HDMI and DP ports of the new VBIOS and the card you’re flashing and make sure they match. Note that this is not a mandatory step but you may lose ports if they are different.
  * When you flash a VBIOS, the V/F curve and fan curve will be different so your current overclock may not be stable or lower than usual and the fan speeds may be different.
  * If your power goes out while flashing, there is a chance of bricking your card just like a motherboard BIOS flash.
 ## How to Flash a VBIOS
  * Download [GPU-Z](https://www.techpowerup.com/gpuz/) and go to [Advanced](https://cdn.discordapp.com/attachments/721078648911954103/932752065657200700/unknown.png) -> [NVIDIA BIOS](https://cdn.discordapp.com/attachments/721078648911954103/932752453735174214/unknown.png) -> 	[Power Limit](https://cdn.discordapp.com/attachments/721078648911954103/932752933966200872/unknown.png) -> [Maximum](https://cdn.discordapp.com/attachments/721078648911954103/932753077902131220/unknown.png).
  * After you have followed the steps above, go [here](https://www.techpowerup.com/vgabios/) and locate a suitable VBIOS with a higher power limit for your card.
  ![image](https://user-images.githubusercontent.com/69487009/155030699-7616020e-ac97-4ae0-9b26-9bd0ff8a379c.png)
  * There may be some XOC VBIOSes with a 1000w power limit but these are highly discouraged unless you know exactly what you are doing and have sufficient cooling/power.
  * Once you have found a VBIOS, download it as well as [NVFlash](https://www.techpowerup.com/download/nvidia-nvflash/).
  * Create a new folder in your home directory with any name and put the ROM and the contents of the extracted NVFlash folder inside of it. The folder should look like this. 
   
  ![image](https://user-images.githubusercontent.com/69487009/155030951-b4ed2a12-f5e5-4e15-a655-73116b429701.png)
  * Shift right-click inside the folder and select Open in Windows Terminal/Powershell.
  * Once the window is open, type `./nvflash64.exe --save example.rom`
    * Two dashes before save
  * Then type `./nvflash64.exe -6 `(type the first letter of the ROM and hit tab to complete)
    * One dash before 6.
  * Type “y” when prompted (twice) and keep in mind that your screen will flash/go black for a moment.
 ## VBIOS Troubleshooting
  * If the VBIOS failed to flash and you confirmed all the prerequisites to flashing, type `./nvflash64.exe —protectoff` before flashing.
  * If that still fails to work, try [this](https://www.techpowerup.com/download/nvidia-nvflash-with-board-id-mismatch-disabled/) version of NVFlash.

# Miscellaneous
 ## Fixing a Boot Loop
  * Hold down shift and click restart.
  * At the choose an option screen, go to Troubleshoot > Advanced options > Startup Settings > Restart. Finally, type 4 to boot into safe mode.
  
  ![image](https://user-images.githubusercontent.com/69487009/155035875-c7a04198-6f72-45a8-8c81-af7b1bac496e.png)
  * Go into MSI Afterburner and uncheck this to have your overclock not applied at startup. If you have this checked, uncheck it as well.
  ![image](https://user-images.githubusercontent.com/69487009/155035951-3d926aaf-ffb4-44db-9910-844f8b7ad50d.png)
  ## NVCleanstall/DDU
  This is used when you suspect your drivers are causing issues and/or you just want a less bloated driver.
   * Install the [latest drivers](https://www.nvidia.com/Download/index.aspx), [DDU](https://www.guru3d.com/files-details/display-driver-uninstaller-download.html), and [NVCleanstall](https://www.techpowerup.com/download/techpowerup-nvcleanstall/). 
   * Unplug your Ethernet/turn off Wi-Fi to ensure that Windows doesn’t install drivers on its own.
   * Hold down shift and click restart. Go to Troubleshoot > Advanced options > Startup Settings > Restart.
   * Finally, type 4 to boot into safe mode.
   * Run DDU, select GPU as the device, and click clean and restart.
   * Boot into your computer like normal and run NVCleanstall.
   * Select use driver files on disk and select the driver that you installed earlier.
   * Make sure everything is unchecked except for PhysX, and maybe HD audio via HDMI/USB-C Driver if you use those.
   * Click next and uncheck everything other than Disable Installer Telemetry & Advertising. Lastly, click install and your drivers will install.
 
# Tips and Tricks
 * The most important thing about overclocking is experimentation, try different things like increasing voltage to get higher clocks or lower voltage to get lower temps and more consistent clocks.
 * Temps are important. GPUs should stay as cool as possible for longevity, audibility, and performance:
   * For starters, taking off your side panel can improve thermals in airflow limited scenarios; if they do, a case with more airflow will help thermals considerably.
   * Repasting your GPU with a high-quality paste such as NT-H2, KPX, and GELID GC Extreme. It’ll last a long time and has an incredible impact on temperatures.
   * Deshrouding and adding fans such as Phanteks T30s, Noctua NF-A12x25s, or ARCTIC P12s (budget) are also a good way to improve temps as stock fans tend to not be that great.
   * A more aggressive fan curve on your CPU, GPU, or case can help with airflow and thermals. Go as high as your audibly tolerable.
   * Removing dust filters can help with airflow due to the misalignment of holes. 
