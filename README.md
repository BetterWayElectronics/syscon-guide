<h2>Syscon Guide</h2>
<b>What even is this?</b> Well its a guide on how to read and write your PS4's Syscon (albeit writing is on a new chip for this guide).
<br><b>Why Tho?</b> You can downgrade (via CoreOS swapping) and repair LoadBIOS type corruptions. You can also enable service mode!
<br><b>Where's the rest of the guide?</b> It is TBA, but my software handles most of the downgrade process anyways.
<br><br>
<b>Note:</b> You <i>can</i> write to the original chip but requires a totally different method and requires a pre-flashed arduino that you must <b><a href="https://betterwayelectronics.com.au/bweps4sysconwriter">purchase from BwE</a></b>. 
<br>The new method has its own unique exploit that reads/writes SCE chips on-board. If you want to do this, then this guide is not for you.
<br>The benefit of this new method is that it requires only 2 wires (initially to glitch) to the syscon then 3 to alternative points. Read and write the original chip on the board. No desoldering!
<br>The target market for this are repairers who will constantly be downgrading or fixing LoadBIOS errors. This will then remove the need to constantly desolder/resolder and buy chips.
<br>
<br>Preview the paid method's guide <a href="https://betterwayelectronics.com.au/sce_syscon.html">here</a>
<br>
<h3>Shopping List</h3>
<b>Required:</b>
	<li><a href="https://www.aliexpress.com/item/1005004448662741.html">Arduino Nano v3 ATMEGA168P (OR 328P) w/ CH340 ($6.50AUD)</a>
	<li><a href="https://www.aliexpress.com/item/32273550144.html?mp=1">FT232RL TTL Serial Module ($2AUD)</a>
	<li><a href="https://www.aliexpress.com/item/1005001437032289.html">Multi LQFP (64-100) to DIP Board ($4AUD)</a>
	<li><a href="https://www.aliexpress.com/item/32416951874.html">Breakable Pin Headers (Any Nice Colour) ($0.80AUD)</a>
	<li><a href="https://www.aliexpress.com/item/32214404363.html">x2 Colourful Mini Breadboards ($1AUD)</a>
	<li><a href="https://www.aliexpress.com/item/4000203371860.html">Male->Female Dupont Cables ($2AUD)</a>
	<li><a href="https://www.aliexpress.com/item/32247209964.html">220ohm Resistor ($1AUD)</a>
	<li><a href="https://www.aliexpress.com/item/32660088529.html">x2 1N4148/1N4448 Diodes ($2AUD)</a>
	<li><a href="https://www.betterwayelectronics.com.au/downloads/Syscon.rar">Requisite Software (Reader, Writer, Verifier, Patcher)</a>
</li>
<br>
<b>Optional:</b>
	<li><a href="https://www.aliexpress.com/item/1005002888994993.html">LQFP64 to DIP Board ($4AUD)</a>
	<li><a href="https://www.aliexpress.com/item/1762279813.html">LQFP64 Socket Adapter ($45AUD)</a>
	<li><a href="https://www.aliexpress.com/item/1005003352270633.html">LQFP100 Socket Adapter ($45AUD</a>
</li>
<br>
<b>Soldering, Whats That?:</b>
  <li><a href="https://www.aliexpress.com/item/4001063621549.html">T12-942 QUICKO Soldering Station (SET 5) ($58AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/1005004623323483.html">DC24v 6A Adapter for Soldering Station ($28AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/32948598235.html">Fake Amtech Flux ($7AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/1005004532993074.html">Lead Solder Low-ish Melt ($3AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/33022639575.html">Solder Wick ($1AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/1005003102463009.html">Love Heart Tweezers ($7AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/4000315816666.html">32-34AWG Cable 10m ($4.50AUD)</a></li>
  <li><a href="https://www.aliexpress.com/item/1005001900973775.html">Atten ST0862D Hot Air Station ($257AUD) (You Can Avoid This With ChipQuik)</a></li>
  <li><a href="https://www.aliexpress.com/item/4000123318936.html">SMD Vacuum Pen ($1AUD)</a></li>
</li>
<h3>Compatibilitiy</h3>
<img src="https://i.imgur.com/4fpFJvI.jpg" width="50%" height="50%"><br>
Do you have the Syscon on the right? You're outta luck. The glitch only works on Renesas RL78 chips. The guide ends here.<br>
The chip MUST have A0#-COL or A0#-COL2 where the # is a number, obviously.

<h3>Syscon Types & Pinout</h3>
<li>With this method that's provided you need to replace Sony's Syscon chip with a new one.
<li>Why? Well this method is based on the public <a href="https://github.com/VV1LD/SYSGLITCH">glitch</a> and its function is to glitch to dump, <b>not to write</b>.
<li>You can however easily write to a fresh blank R78 chip with a TTL device very easily.
<li>You must then buy one of the below chips from whatever source you can find. I have about 50-100 in total, so I may be able to supply some if you cannot find any.
<br><br>
<table>
  <tr>
    <th>FAT</th>
    <th>SLIM/PRO</th>
  </tr>
  <tr>
    <td>R5F100PLAFB</td>
    <td>R5F100LLAFB</td>
  </tr>
  <tr>
    <td>R5F100PLDFB</td>
    <td>R5F100LLDFB</td>
  </tr>
  <tr>
    <td>R5F100PLGFB</td>
    <td>R5F100LLGFB</td>
  </tr>
  <tr>
    <td>R5F101PLAFB</td>
    <td>R5F101LLAFB</td>
  </tr>
  <tr>
    <td>R5F101PLDFB</td>
    <td>R5F101LLDFB</td>
  </tr>
</table>
<br>

<div style="display: flex;">
  <div style="width: 420px; padding: 10px;">
    <img src="https://i.imgur.com/UnGh1ne.png" width="45%" height="45%">
    <br><b>FAT Syscon</b>
  </div>
  <div style="width: 420px; padding: 10px;">
      <img src="https://i.imgur.com/mzsNJHP.png" width="45%" height="45%">
    <br><b>Slim/Pro Syscon</b>
  </div>
</div>
<br>

<h3>Wiring To Syscon & Removing/Replacing</h3>
Pinout:<br>
<table>
  <tr>
    <th>5v</th>
    <th>GND</th>
    <th>D4</th>
    <th>D2</th>
    <th>TXD</th>
    <th>RXD</th>
  </tr>
  <tr>
    <td>EVVD0 (Lift if on board)</td>
    <td>EVSS0</td>
    <td>VDD (Lift if on board)</td>
    <td>RESET</td>
    <td>220ohm Resistor</td>
    <td>TOOL0</td>
  </tr>
  <tr>
    <td>Pin 16 Pro</td>
    <td>Pin 14 Pro</td>
    <td>Pin 15 Pro</td>
    <td>Pin 6 Pro</td>
    <td>RXD (Arduino)</td>
    <td>Pin 5 Pro</td>
  </tr>
  <tr>
    <td>Pin 23 FAT</td>
    <td>Pin 21 FAT</td>
    <td>Pin 22 FAT</td>
    <td>Pin 13 FAT</td>
    <td></td>
    <td>Pin 12 FAT</td>
  </tr>
</table>
</ol>
<br>
<img src="https://i.imgur.com/3pRzA2h.png" width="45%" height="45%">
<br><b>Schematic</b>
<br>
<img src="https://i.imgur.com/66tC1WL.jpeg" width="45%" height="45%">
<br><b>Dumping off-board example</b>
<br>

<img src="https://i.imgur.com/E6sxlx4.jpeg" width="45%" height="45%">
<br><br>
<li>If you are dumping on board, <b>lift pin 15 and 16</b>. To do this add flux and low melt solder to the pins and let it soak in.
<li>Use tweezers and a thin tip and while applying heat to the pin push from behind with the tweezers until the pin is lifted.
<li>Wire pin 5 and 6 flat against the resistors, directly to the pins or the alternative solder points. Following best practice.
<br><br>
<li>To remove the Syscon chip entirely, apply flux to all of the pins and flood them with low melt solder (chipquik if not using hot air).
<li>Apply 480c at 40% pressure from a height of approximately 15cm until the solder is visibly liquidous on all sides.
<li>Pull up the chip with an SMD vacuum pen.
<li>Tin the pads on the PS4 with low melt solder.
<li>Clean pins 1-16 on the Syscon of any solder bridges and solder to pre-tinned breakout board (or place into DIP socket).
<br><br>
<li>When reattaching New & Blank Syscon first apply a light layer of flux on the already tinned pads.
<li>Line up Syscon appropriately or solder each corner manually to ensure the chip does not move during reflow.
<li>Apply 480c at 40% pressure from a height of approximately 20cm and slowly drop until you see flux bubble/move and solder shine/glimmer.
<li>If you do not want to use hot air, use drag soldering technique or manually solder each pin individually with thin tip tinned with low melt solder.
<br><br>
<li>When reading Syscon on board (after patching) <b>wire only pin 5, 6 and ground</b> either directly to the chip or alternative points.

<div style="display: flex;">
  <div style="width: 380px; padding: 10px;">
    <img src="https://i.imgur.com/oqQqFas.jpeg" width="45%" height="45%">
    <br><b>Soldering ALL pins to Syscon for dumping on-board (Not required)</b>
  </div>
  <div style="width: 380px; padding: 10px;">
    <img src="https://i.imgur.com/oqYIJ17.jpeg" width="45%" height="45%">
    <br><b>Dumping on-board example</b>
  </div>
</div>

<h4>Best Practice</h4>
<div style="display: flex;">
  <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/pjizFZc.png" width="45%" height="45%">
    <br><b>Solder the jumper wires flat against the legs.</b>
  </div>
  <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/wm4PrwP.png" width="45%" height="45%">
    <br><b>The entire jumper wire must fill the entire pad.</b>
  </div>
  <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/nXx3oep.png" width="45%" height="45%">
    <br><b>The wire must be parallel to the component termination.</b>
  </div>
</div>

<h3>Reading Syscon (Currently ONLY works on A0#-COL/2 chips):</h3>
<img src="https://i.imgur.com/zV8EvTU.png" width="55%" height="55%">

  <li>Connect from your Arduino to the Syscon Chip (See Wiring To Syscon Below)
  <li>Launch BwE_PS4_Syscon_Reader.exe in Terminal with your COM port (Eg: BwE_PS4_Syscon_Reader.exe COM4)
  <li>It will glitch the chip (if this is your first read and you have not enabled OCD mode) and then dump!
  <li>It will then re-dump and compare in order to validate them.
  </li>
  <br>If the dumps do not match change resistors (100ohm, 510ohm, 1kohm).
  <br>If it does not even dump check your connections (seriously) or change your Octocoupler.

<h3>Patching Syscon Dump:</h3>

<ol>
  <li>Run BwE PS4 NOR Validator
  <li>Select Option 2 - Scan & Patch PS4 Syscon
  <li>Optional: Select Verbose Mode (Only required for Manual Patching)
  <li>Syscon will scan for a patchable slot, if there is one available it will say at the bottom in "Final Results".
  <li>If it says "Active Slot Patchable" select Option 1 "Auto Patch"
  <li>If it says "Unable to Auto-Patch" it will prompt you to Manually Patch - If so you must select an earlier 080B (Use Verbose Mode) to overwrite the last 080B.
  <li>If it says "Syscon NOT Patchable" then call it quits, game over. Your PS4 has either had its initialisation overwritten or some other historical event is blocking the patch.
  <li>Apply the patch!
  <li>It will show you what you are overwriting (and potentially the data you are overwriting it with).
  <li>File will be saved as "???_080B_patched.bin" - Keep this and the original, label it appropriately and store it!
</ol>

<img src="https://i.imgur.com/s8X8hKA.png" width="45%" height="45%">

<h3>Programming Blank Syscon:</h3>

<ol>
  <li>Connect from your TTL to the Syscon Chip (R5F100LLAFB for Slim/Pro OR R5F100PLAFB for FAT):
    <ol type="a">
      <li><strong>VDD</strong> -> VDD (Pin 15/Pin 22 FAT) & EVVD0 (Pin 16 Pro/Pin 23 FAT) (Remove If On-Board)</li>
      <li><strong>GND</strong> -> EVSS0 (Pin 14 Pro/Pin 21 FAT) (To Common GND If On-Board)</li>
      <li><strong>RTS (or DTR)</strong> -> 1N4148/1N4448 -> RESET (Pin 6 Pro/Pin 13 FAT) (Diode Not Required - Remove If Timeout)</li>
      <li><strong>TXD</strong> -> 1N4148/1N4448 -> RXD (TTL) (Keep Diode On Outside Slots Of BreadBoard)</li>
      <li><strong>RXD</strong> -> TOOL0 (Pin 5 Pro/Pin 12 FAT)</li>
    </ol>
  </li>
  <br><img src="https://i.imgur.com/6VUH3ju.png" width="45%" height="45%">
  <br>
  <li>Install Renesas Flash Software</li>
  <li>Convert dumped/patched Syscon .bin File to S28 via HXD's (Or Other HexEditor's) Export Option</li>
  <li>Load Pro/FAT (LLAFB/PLAFB) project file in Renesas Flash Programmer & Load your S28 Dump</li>
  <li>Set 'Reset Settings' in 'Tool Details' to RTS & Invert or DTR & Invert depending on your TTL Device (RTS is preferred)
  <li>In 'Operation Settings' set 'Command' to 'Erase, Program, Verify' and 'Erase Options' to 'Erase Chip' and in 'Program & Verify' to 'Erase'.
  <li>'Flash Options' should all be set to NO.
  <li>'Connect Settings' should be '1 Wire UART' @ '115200bps' and on your correct COM port
  <li>Start!</li>
</ol>
<br>
<img src="https://i.imgur.com/7U27vFA.jpeg" width="45%" height="45%">
<br><b>Example</b>
<br>

<h3>Reading & Writing NOR:</h3>

<li>Dump the NOR using SPIWay (illustrated below) or through a CH341A or other programmer.
<li>You can either solder directly to the pins, their resistors/pads and dump/flash on-board (<b>@ ~3.0v Only</b>) or remove the chip entirely.
<li>You can also follow <a href="https://repair.wiki/w/PS4_UART_Guide">this guide</a> on the Repair Wiki in which I illustrate the process behind enabling UART (which you should do).

<img src="https://i.imgur.com/8t7iBVp.png" width="45%" height="45%">

<table border="#999" cellspacing="0" cellpadding="5" class="wikitable" style="border:1px solid #999; border-collapse: collapse;">

<tbody><tr bgcolor="#cccccc">
<th>8-Pin</th>
<th>16-pin</th>
<th>Usage</th>
<th>Teensy++ 2.0<br />SPIway</th>
<th>Description
</th></tr>
<tr>
<td>-</td>
<td>1</td>
<td>SIO3</td>
<td>B5</td>
<td>8pin: Not Available - not used / 16pin: Serial Data Input &amp; Output (for 4xI/O read mode)
</td></tr>
<tr>
<td>8</td>
<td>2</td>
<td>VCC</td>
<td>+5V pad</td>
<td>+3V DC Power Supply
</td></tr>
<tr>
<td>7</td>
<td>3</td>
<td>HOLD#/RESET#</td>
<td>B6</td>
<td>8pin: Hold, to pause the device without deselecting the device / 16pin: Hardware Reset Pin Active low
</td></tr>
<tr>
<td>-</td>
<td>4</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>-</td>
<td>5</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>-</td>
<td>6</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>1</td>
<td>7</td>
<td>CS#</td>
<td>B0</td>
<td>Chip Select
</td></tr>
<tr>
<td>2</td>
<td>8</td>
<td>SO/SIO1</td>
<td>B3</td>
<td>Serial Data Output (for 1 x I/O) or Serial Data Input &amp; Output (for 2x I/O or 4x I/O read mode)
</td></tr>
<tr>
<td>3</td>
<td>9</td>
<td>WP#/SIO2</td>
<td>B4</td>
<td>Write Protection: connect to GND or Serial Data Input &amp; Output (for 4x I/O read mode)
</td></tr>
<tr>
<td>4</td>
<td>10</td>
<td>GND</td>
<td>GND</td>
<td>Ground
</td></tr>
<tr>
<td>-</td>
<td>11</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>-</td>
<td>12</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>-</td>
<td>13</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>-</td>
<td>14</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">NC</td>
<td style="color:white; background-color:darkgrey;">No Connection
</td></tr>
<tr>
<td>5</td>
<td>15</td>
<td>SI/SIO0</td>
<td>B2</td>
<td>Serial Data Input (for 1 x I/O) or Serial Data Input &amp; Output (for 2x I/O or 4x I/O read mode)
</td></tr>
<tr>
<td>6</td>
<td>16</td>
<td>SCLK</td>
<td>B1</td>
<td>Clock Input
</td></tr>
</tbody></table>

<br>
<div style="display: flex;">
  <div style="width: 320px; padding: 10px;">
    <img src="https://www.psdevwiki.com/ps4/images/thumb/f/fa/MX25L1006E_Pinout.png/800px-MX25L1006E_Pinout.png" width="45%" height="45%">
    <br><b>8 Pin WSON8 - Pro & Slim</b>
  </div>
  <div style="width: 320px; padding: 10px;">
    <img src="https://www.psdevwiki.com/ps4/images/thumb/c/cd/MX25L25635FMI-10G_Pinout.png/800px-MX25L25635FMI-10G_Pinout.png" width="45%" height="45%">
    <br><b>16 Pin SOP16 - Fat</b>
  </div>
</div>
<br>
<div style="display: flex;">
  <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/cI0WcwT.jpeg" width="45%" height="45%">
    <br><b>Hardwiring Example</b>
  </div>
  <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/wPHOhBY.jpeg" width="45%" height="45%">
    <br><b>Non-Invasive Method</b>
  </div>
    <div style="width: 320px; padding: 10px;">
    <img src="https://i.imgur.com/wtgghfk.jpeg" width="45%" height="45%">
    <br><b>2.8v CH341A Mod</b>
  </div>
</div>


<h3>Patching NOR Dump:</h3>

<ol>
  <li>Run BwE PS4 NOR Validator</li>
  <li>Select Option 1 "Validate or Patch PS4 NOR"1</li>
  <li>Select your NOR file</li>
  <li>Select Option 9 "Validate" and patch for UART when prompted</li>
  <li>If your NOR is valid go back and select Option 4 "Patch CoreOS & Southbridge (LoadBios & Downgrading)"</li>
  <li>Read the warnings!</li>
  <li>Select Option 1 "Patch SB Flag & CoreOS Header"</li>
  <li>Select CoreOS Header Patch - There are multiple choices as each console may behave differently with each patch, just go with the first.
  <li>NOR will be saved as "?_sb-coreos-patched.bin"</li>
  <li><b>Do NOT boot the console with patched NOR until you have ALSO patched the Syscon.</b>

</ol>

<img src="https://i.imgur.com/d7ANNtH.png" width="65%" height="65%">

<h3>Final Step - LoadBios Repair / Downgrade:</h3>

There are two methods, both are basically the same so pick whichever suits you!
<br><br>
<li>Patch the NOR with SB & CoreOS patch of your choice
<li>Boot console and read UART log
<li>If UART log says "CheckUpdVersion" AND OR the Bootloader version has changed...
<li>Write the Syscon patch to the console
<li>If not, try another patch and repeat the process
<li>On success the console will boot to safe mode and prompt to install lower firmware (recovery).
<br>
<br>The other method:
<br><br>
<li>Patch the NOR with SB & CoreOS patch of your choice
<li>Write the Syscon patch to the console
<li>If the console does not boot...
<li>Repeat first two steps, pick a new Patch for NOR and keep the same patch for Syscon.
<li>On success the console will boot to safe mode and prompt to install lower firmware (recovery).
<br>
<br>Troubleshooting:
<br><br>
<li>If you still have loadBios -8 and the Bootloader version has changed you have an issue with your RAM, replace and or repair it.
<li>If you have BlStorageHeader error, you did not follow my instructions and have soft bricked your syscon, I will have to patch for you -- for $$$$ (or wait for update to my software).
<br>
<h3>Credits/Greetz:</h3>
DARKNESMONK
  <br>PDJ
  <br>Hoea
  <br>Donators & Suppliers of Dumps/Syscons
