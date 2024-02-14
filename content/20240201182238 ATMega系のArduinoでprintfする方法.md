# 20240201182238 ATMega系のArduinoでprintfする方法
#tech #arduino #printf

いつも忘れるのでメモ。
この、`fdevopen`を使う方法は、この関数がAVR用のavr-libcでしか定義されていないため、
ESP32やARMなど他のMCUがベースになっている場合には使えないので注意。

Aruino UNO3、 Arduino Nano、Pro Microなどでは使える。

```cpp
// 名前はなんでもよい
int my_putc( char c, FILE *t) {
  return Serial.write( c );
}

void setup()
{
    Serial.begin(115200);
    fdevopen( &my_putc, 0);
    // 以降printfが使える。例↓
    print("Hello world! A0 = %d\n", analogRead(0));
}

void loop()
{

}
```

cf.

- <https://forum.arduino.cc/t/how-to-make-printf-work/6456>
- <https://cega.jp/avr/avr-libc_list/>


