# KSNProjekt
KSN_Project_Mark_Gottlieb 

## AM_Modulation
![alt text](https://github.com/MarkGottlieb/KSNMark/blob/main/AM_modilation.png)
Das Bild zeigt einen typischen Aufbau eines AM-Modulationsschemas in Gnu Radio, einer visuellen Programmierumgebung für die Signalverarbeitung. Hier ist eine kurze Erklärung jedes Teils und wie sie zusammenarbeiten, um AM-Modulation zu erreichen:
Das Bild zeigt einen typischen Aufbau eines AM-Modulationsschemas in Gnu Radio, einer visuellen Programmierumgebung für die Signalverarbeitung. Hier ist eine kurze Erklärung jedes Teils und wie sie zusammenarbeiten, um AM-Modulation zu erreichen:

+ **Variable (samp_rate):** Dies definiert die Abtastfrequenz, die in diesem Fall 48kHz beträgt. Das ist die Rate, mit der das Signal verarbeitet wird.

+ **QT GUI Range (Frequency1, Volume, Frequency2, Modulation):** Diese Blöcke stellen grafische Benutzeroberflächen (GUI) dar, die es dem Benutzer ermöglichen, Parameter wie Frequenzen, Volumen und Modulationstiefe in Echtzeit zu steuern. Das hilft beim Testen und bei der Demonstration der Effekte der AM-Modulation.

+ **Wav File Source:** Dieser Block liest ein Audiosignal von einer WAV-Datei ein. Das Signal könnte Musik oder gesprochene Worte sein, und es wird als Modulationssignal verwendet.

+ **Signal Source:** Erzeugt die Trägerwelle, die typischerweise eine Kosinus-Welle ist, mit einer Frequenz und einer Amplitude, die über die GUI eingestellt werden kann.

+ **Add Const:** Fügt eine Konstante zum Signal hinzu. Dies wird oft gemacht, um sicherzustellen, dass das modulierte Signal immer positiv ist, besonders wenn die Modulationstiefe sehr hoch ist.

+ **Multiply:** Hier wird das Trägersignal mit dem Audiosignal (vom WAV File Source) multipliziert. Durch diese Multiplikation wird die Amplitude der Trägerwelle entsprechend den Amplitudenänderungen des Audiosignals geändert – das ist der Kern der AM-Modulation.

+ **Audio Sink:** Dieser Block gibt das modulierte Signal an die Soundkarte des Computers aus, so dass man es hören kann.

+ **QT GUI Sink:** Dies zeigt das Spektrum des Signals in einem Frequenzspektrum-Display an. Man kann die modulierten Signale visuell überprüfen und bestätigen, dass die Amplitudenmodulation wie erwartet funktioniert.
    
## FM_Radio
![alt text](https://github.com/MarkGottlieb/KSNMark/blob/main/fm_radio.png)

+ **PlutoSDR Source:** Dieser Block ist eine Quelle für das FM-Signal, das von einem Software Defined Radio (SDR), dem PlutoSDR, empfangen wird. Es definiert die Sample Rate (2M, also 2 Millionen Samples pro Sekunde), die Zentralfrequenz (z.B. 107.5M für 107,5 MHz, die typische Frequenz eines FM-Radiosenders) und andere wichtige Eigenschaften des empfangenen Signals.

+ **QT GUI Range (freq_center):** Ein GUI-Element, das dem Benutzer erlaubt, die Zentralfrequenz des Empfängers einzustellen. Man kann damit durch den FM-Bandbereich scrollen, um verschiedene Stationen zu finden.

+ **Rational Resampler:** Ändert die Sample Rate des empfangenen Signals. Dies ist notwendig, um die Verarbeitung des Signals auf eine passende Sample Rate für die Weiterverarbeitung anzupassen.

+ **Low Pass Filter:** Filtert unerwünschte Frequenzen aus dem Signal heraus, um nur das gewünschte Signal zu erhalten. Dies reduziert Bandbreite und Rauschen.

+ **QT GUI Frequency Sink und QT GUI Waterfall Sink:** Diese GUI-Elemente zeigen eine visuelle Darstellung des Signals sowohl im Frequenzbereich (Frequency Sink) als auch als "Waterfall" Display, das eine Zeit-Frequenz-Darstellung des Signals ist. Das hilft, das Signal zu analysieren und zu überwachen.

+ **WBFM Receive:** Ein Block speziell für den Empfang von Wideband FM Signalen. Es dekodiert das FM-Signal in ein Basisband-Audiosignal.

+ **Rational Resampler (erneut):** Passt die Sample Rate des dekodierten Audiosignals an die Sample Rate an, die für die Audioausgabe benötigt wird (hier: 48 kHz).

+ **Audio Sink:** Gibt das dekodierte Audiosignal aus, sodass es über Lautsprecher oder Kopfhörer hörbar ist.
