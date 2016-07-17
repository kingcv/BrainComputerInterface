# BrainComputerInterface
Making brain controlled tv remote
FOLLOW THE STEPS FOR CREATING THE PROJECT

Step 1
Gather The Parts


If you want to follow along with this project here’s a list of parts you will probably need to order. The more parts that you already have, the cheaper this project will be.

    Star Wars Force Trainer= $40
    Arduino = $7
    IR Receiver/IR LED = $0 (scavenged from old VCR)
    100k ohm resistor/various wires = $0 (already had/scavenged)

Step 2
Disassemble the Force Trainer
In order to use the brain waves that the Star Wars Force Trainer receives, we need to take it apart and connect to it. All we will need is the headset. The ball tube will not be used for this project. One of the best things about this project is that it still functions as a toy even after you’ve hacked it. So you don’t have to worry about not being able to play with it again once you’ve taken it apart.

    On the headset, remove the batteries and the screws that hold the top plate on.
    Locate the Neurosky EEG board, as pointed out on the left.
    Solder a wire to the T-Pin on the EEG board.
    Solder a second wire to the Ground terminal on the battery case.
    Drill or carve a small hole in the plastic casing that the wires can run through.
    Put a small dab of hot glue on the wires after running them through the hole to hold them in place.

Now you’re headset should be ready for outputting data! Replace the batteries and ensure everything is still working, and then screw the top casing back on. The next part is connecting an Arduino to the headset to collect the data!

Step 3
Connecting the Arduino

 
The next step is to get the EEG data from the headset onto our computers. In order to do this, we need something that will convert it from raw data coming from wires to readable data coming through USB. We’ll be using an Arduino for this. And here’s the steps we’ll need to take to connect it all.

    If you like, you can fasten the Arduino to the top of the headset using tape or zip ties.
    Connect the T pin wire from the headset to the RX pin on the Arduino.
    Connect the Ground wire from the headset to a Ground pin on the Arduino.
    Using a USB cable, connect the Arduino to your computer.
    Download and install the Arduino software version 1.0.5. The software doesn’t work with any newer versions.
    Before starting up the software, download and install the Arduino Brain library. You want to place it in your Arduino Libraries folder.
    Startup the software and load up the test program by going to File > Examples > Brain > BrainSerialTest
    Upload it to the Arduino (you may have to temporarily remove the RX wire in order to do this)
    Open up the serial console, put the headset on your head, turn it on, and see what results you get!
    The first number is the signal strength, the second is the attention value, and the third is the mediation value.



Step 4
Creating the IR Remote


o we have the headset connected to the computer, and we are now viewing and collecting our brain wave data, but now what do we do with it? One solution is to connect an LED to the ground and 13 pins on the Arduino and to upload the BrainBlinker example program to the Arduino. But the solution we’re choosing for this tutorial is creating an IR remote. In order to do that, however, we first need to mimic a remote. Here’s the steps you’ll need to take in order to do that.

    In order to test this out, you may want to remove the headset wires from the Arduino for the time being.
    The first thing you need to do is acquire an IR receiver and an IR LED. You can purchase them, or you can usually salvage them from old electronics (such as VCR’s).
    Connect the IR Receiver Ground pin to a Ground pin on the Arduino, the power pin to the 5v pin, and the data pin to pin 11.
    Connect the IR LED Ground pin to a Ground pin on the Arduino, and the power pin to a 100 ohm resistor and then to pin 3 on the Arduino.
    Then connect the Arduino to the computer.
    Before starting up the Arduino software, download the Arduino IR Library software and install it in your Arduino Libraries folder.
    After loading up the Arduino software, paste in the following program:


Once this program is uploaded to your Arduino, open up the serial monitor, point a remote at the IR receiver and start pressing buttons. You should see a response in the results in the serial monitor screen. This will be the button code. You want to write down this code for later use (ex: NEC: 10EF22DD)

After you have the button code or codes that you want to use, we now need to see if we can send those codes to the IR led and see if they work.

    In the Arduino software, load the File > Examples > IRremote > IRsendDemo program.
    Replace the “irsend” command with the code from the button you want to emulate.
        Example: irsend.sendNEC(0x10EFA05F, 32);
    Upload this new program to the Arduino and place it next to the object you want to control.
    In the Arduino software, open up the serial monitor, type in some text and click “send”.
    If all goes well, a signal should be sent through the LED and should be received by the object you want to control.

