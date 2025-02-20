from pynput import keyboard
from pynput.keyboard import Controller
import time
import threading

dd = int(input("Delay Giriniz (5 ila 30 tavsiye ediyorum.): "))
md = dd / 1000

print("=============truquamacro==============")


keyboard_controller = Controller()

is_macro_active = False

def macro_action():
    while True:
        if is_macro_active:
            keyboard_controller.press('ı')
            time.sleep(md)
            keyboard_controller.release('ı')
            time.sleep(md)  
            
            keyboard_controller.press('o')
            time.sleep(md)
            keyboard_controller.release('o')
            time.sleep(md)  
        else:
            time.sleep(md)

def on_press(key):
    global is_macro_active
    try:
        if key.char == 'x':  
            is_macro_active = True
            print("Makro başlatıldı.")
    except AttributeError:
        pass

def on_release(key):
    global is_macro_active
    try:
        if key.char == 'x':  
            is_macro_active = False
            print("Makro durduruldu.")
    except AttributeError:
        pass


macro_thread = threading.Thread(target=macro_action)
macro_thread.daemon = True
macro_thread.start()


with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
