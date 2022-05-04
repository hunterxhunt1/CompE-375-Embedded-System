# Embedded-System

COMPE 375 Projects

These codes are test by using the Atmega328 P/PB. 
Content within these files:

- UART

The program is supposed to take in my Red ID as characters and send them through the USART port on our AVR Xplained miniboard. First it sets the Baud Rate by using the equation .Then, a function named USART_int(void) sets the UBRR0H and UBRR0L to 1 and the baud rate respectively. We also enable the receiver/transmitter pins, and set an 8 bit data frame and a 1 bit stop mode. With that, it is called into main in order to read, transcribe, and transfer my Red ID. The program checks to see if the buffer is empty before sending/receiving data, so no data is lost. 

I used an unsigned char to hold my Red ID. I used the RXE and TXE to receive and transmit data respectively. I also used the UBRR0H, UBRR0L, UCSR0B, UCSR0C, USBS0, UCSZ00, UCSZ01, UCSR0A, UDRE0, and UDR0 registers. Finally, it also uses the _delay_ms() variable.


- Keypad Multiplexing

The program is supposed to take inputs from the keypad, and transmit that information to the Atmega board and display it on the serial port test. The rows and columns are assembled by PORTD [4 - 7] and PORTB [0 - 3] respectively. We use the rows as our inputs and columns as our outputs, because the keypad only has 8 pins to represent 16 characters. The program takes in the de-bouncing situation by adding delays after the data is transferred. The data is then displayed on the data visualizer to see if the program works.

I used the PORTD,PORTB registers as inputs and outputs respectively. I used the DDRB and DDRD to set the data direction for the input and output. I enabled the pull-up resistors to PINB. UBRRL and UBRRH for the 8 bit shift and to set the baud rate. UCSR0B, UCSR0C, UCSZ00, and UCSZ01. I used character arrays for the rows, columns, and the characters that pass through the keypad. This is possible because the TXEN0 (transmitter register) is enabled.


- Frequency to Sound Converter

My program converts the frequency values that are inputted from the keypad to the speaker.

I'm using PD3 as the main output, because I am using the timer 2 register. I enabled the Fast PWM registers and non-inverting  mode as my main timer. Since we are using the keypad, I enabled PD4-PD7 as output and PB0-PB3 as input and made them into a matrix form, just like in the Keypad Multiplexing. 


- Changing LED Brightness Through Interrupts

My program is supposed to take the input values from the keypad to adjust the brightness of the LED using interrupts and timer registers.

I used the Timer 0 (TCCR0A/B) and timer 2 (TCCR2A/B) register to enable CTC mode and declare my OCR0A,OCR2A,and OCR2B. As for the interrupts, I had the sei() and cli() variables to enable the global interrupts and clear the interrupt flag respectively. I also enabled PD4-PD7 as outputs and PB0-PB2 as inputs to enable the keypad inputs. Finally, I used the ISR() function for the keypad scan and the LED on/off. 

- EEPROM Programming

My program changes the brightness of the LED light on the Atmega board whenever it is reconnected to power.

I used timer 0, and eeprom_read_byte() and eeprom_update_byte(), to change the brightness of the LED by 10% every time it is plugged back into the power supply. I also used interrupts.
