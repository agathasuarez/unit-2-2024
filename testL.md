import pyfirmata
from pyfirmata import Arduino
import time
t=100

board = Arduino('/dev/cu.usbserial-1420')
print("Success, Connected to Arduino")

it = pyfirmata.util.Iterator(board)
it.start()
Buttonyes=board.digital[2]
Buttonyes.mode=pyfirmata.INPUT
Buttonno=board.digital[6]
Buttonno.mode=pyfirmata.INPUT
LED= board.digital[13]
LED.mode = pyfirmata.OUTPUT
LED.write(1)



exit()
