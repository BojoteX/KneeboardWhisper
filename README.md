# VoiceAttack Whisper Transcription Setup

This guide will walk you through setting up a system to record your voice in **DCS World** (or any simulator) using **VoiceAttack** and transcribe it using **Whisper**, a powerful speech recognition model. The transcribed text will be copied to your clipboard, allowing you to easily paste it into the **DCS kneeboard** or any other application.

![Kneeboard Whisper](https://raw.githubusercontent.com/BojoteX/KneeboardWhisper/main/kneeboardwhisper.png)

### Prerequisites:
- **Python 3.11** (Install from the Microsoft Store)
- **VoiceAttack** (for controlling the scripts)
- You need to assign CTRL+ALT+P to the Kneeboard pasting option in the controls in DCS. Check the images for reference.

---

## Step 1: Install Python 3.11

1. **Install Python 3.11** from the **Microsoft Store**. You can open a command line and type `python`. If Python isn’t installed, this will usually redirect you to the Microsoft Store page, where you can download it for free.
   
2. **Verify Installation**: After installing, open a command line and type:
   ```bash
   python --version
   ```
   It should display `Python 3.11.x`.

---

## Step 2: Install Required Python Modules

1. Open a **command line** (press `Win + R`, type `cmd`, and press Enter).

2. Install the required Python modules by copying and pasting the following command, then press **Enter**:
   ```bash
   pip install torch --index-url https://download.pytorch.org/whl/cu118
   pip install openai-whisper sounddevice soundfile pyperclip keyboard wcwidth
   ```
   - **Note**: The `torch` installation may take some time as it includes **CUDA support** to leverage your **NVIDIA GPU** for faster processing.

---

## Step 3: Set Up VoiceAttack Commands

To trigger the recording and transcription, you'll need to configure two commands in **VoiceAttack**—one to start recording and one to process the transcription.

### Create the Recording Command

1. Open **VoiceAttack** and click the **Pencil icon** in the top right to enter the profile **Edit Mode**.

2. Click **New Command** (top right).

3. Choose a button or keypress to **start the recording** (I suggest using a HOTAS button or keypress). Ensure the **"When I say"** checkbox is **unchecked**.

4. In the section titled **"When this command executes, do the following sequence:"**, click:
   **OTHER** > **Windows** > **Run an application**, and select **recorder.py**.

5. Click **OK** to save the command.

### Create the Transcriber Command

1. Repeat the same process, but this time configure it to run the **transcriber.py** script.

2. **Important**: If you want the **same button** to trigger the recording when pressed and the transcription when released:
   - In the **transcriber command**, after selecting the controller button, check the box **"Shortcut is invoked only when all keys are released"**.
   
   This ensures that **pressing** the button starts recording and **releasing** it runs the transcription.

3. Click **Apply** to save everything.

---

## Step 4: Test the Setup

1. To verify the setup, hold the configured button (or press the key), say something, and release the button.
2. After releasing, the transcription will be copied to your clipboard. Open **Notepad** and press **Ctrl + V** to paste the transcribed text.

---

## Troubleshooting

### Test the Scripts Manually:

To confirm that the scripts are working properly:

1. Open two command line windows and navigate to the folder where the scripts are located.

2. Run the **recorder** and **transcriber** scripts manually:

   **Window 1** (for recording):
   ```bash
   python recorder.py
   ```

   **Window 2** (for transcribing):
   ```bash
   python transcriber.py
   ```

3. Check the output of each script. If there are any errors, they will be displayed in these command lines.

4. Don't forget to ASSSIGN CTRL+ALT+P to the Kneeboard pasting option in the controls. Check the images for reference.

![Assignments](https://raw.githubusercontent.com/BojoteX/KneeboardWhisper/main/assignments.png)

---

By following these steps, you’ll have a fully functioning system to record your voice and transcribe it into text, using VoiceAttack to control the process hands-free during your DCS sessions.

Enjoy!
