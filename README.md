# Revealing and Embedding Hidden Messages in Audio Files

## Task 1: Revealing the Hidden Code From the Detected File Using the Librosa Library
In this task, we analysed a group of suspicious audio files to determine which of them contained a hidden four-digit code. The project brief mentioned that the code may have been encoded into the ultrasonic range of frequencies using amplitude modulation. Hence, the spectrum of each audio file was analysed to detect the presence of hidden data. 

We developed a Python application to analyse the audio files’ spectrums using the librosa library. After each file was loaded, its fourier transform was computed to generate a frequency spectrum. We focused on the ultrasonic frequency range of above 18000 Hz to check for any significant magnitudes that may tell us about the embedded code. The audio which exhibited the highest ultrasonic magnitude would be flagged as the most suspicious. In our analysis, Ex3_sound4.wav had the highest magnitude and was thus the most suspicious.

Once flagged, the audio was demodulated to decode the hidden message. A carrier wave of 19000 Hz was generated and used to downshift the ultrasonic data back into a human-audible range. Afterwards, the decoded signal was converted into an audio format that allowed the secret code to be audibly verified.

## Task 2: Embedding a Hidden Text Message in an Audio File Using the Least Significant Bit (LSB) Steganography Method
In this task, we made another Python application that can embed a secret message into the audio file, Ex3_sound5.wav, using the Least Significant Bit (LSB) steganography method. We embedded the message “An eye for an eye makes the whole world blind”. We also made a function that can extract the secret message from the embedded audio file.

We embedded the message by converting the ASCII representation of each character into binary, which was then spread across the least significant bits of consecutive audio samples. We used a pseudo random pattern to select non-consecutive samples for embedding, which is controlled by a user-defined random seed. For this task, we used a default of 1 LSB per sample. The modified audio is then saved as Ex3_sound5_steg.wav.

In order to verify our embedding, we also made an extraction function in the application to reverse the embedding. Using the same seed and LSB count, the binary data was reassembled into characters and successfully reconstructed the original message. 