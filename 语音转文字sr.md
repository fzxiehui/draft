https://zhuanlan.zhihu.com/p/92604225



sudo apt-get install -qq python python-dev python-pip build-essential swig libpulse-dev

pip install pocketsphinx

pip install SpeechRecognition

## 文件识别

```python
import speech_recognition as sr

# obtain audio from the microphone
r = sr.Recognizer()
harvard = sr.AudioFile("./audio_files/harvard.wav")
# harvard = sr.AudioFile("./audio_files/jackhammer.wav")
with harvard as source:
    # 噪声抑制
    # r.adjust_for_ambient_noise(source)
    audio = r.record(source)
    # 读 4 秒的音频文件
    # audio = r.record(source, duration=4)
    # 读取 4 秒后的 10 秒音频文件
    # audio2 = r.record(source, offset=4, duration=10)
# recognize speech using Sphinx
try:
    print("Sphinx thinks you said: " + r.recognize_sphinx(audio))
except sr.UnknownValueError:
    print("Sphinx could not understand audio")
except sr.RequestError as e:
    print("Sphinx error; {0}".format(e))
```

## 麦克风

```python
import speech_recognition as sr

# obtain audio from the microphone
r = sr.Recognizer()

mic = sr.Microphone()

with mic as source:
    print("Say something!")
    audio = r.listen(source)


try:
    print("Sphinx thinks you said: " + r.recognize_sphinx(audio))
except sr.UnknownValueError:
    print("Sphinx could not understand audio")
except sr.RequestError as e:
    print("Sphinx error; {0}".format(e))


```
