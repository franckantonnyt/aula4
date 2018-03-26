# aula4

#include <p18F4550.inc>
	
	CONFIG WDT=OFF; disable watchdog timer
	CONFIG MCLRE = ON; MCLEAR Pin on
	CONFIG DEBUG = ON; Enable Debug Mode
	CONFIG LVP = OFF; Low-Voltage programming disabled (necessary for debugging)
	CONFIG FOSC = INTOSCIO_EC;Internal oscillator, port function on RA6 
	
	ORG 0; start code at 0
	GOTO START
	
	CODE ;Seu código começa depois daqui
START
	MOVLW 0xFB
	MOVWF TRISD
	
	MOVF PORTD, W
	MOVWF 0x00
	RLCF WREG
	ANDWF 0x00, W
	RLCF WREG
	MOVWF PORTD
	
	GOTO START
    END
