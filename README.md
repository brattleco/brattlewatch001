$regfile = "m32def.dat"
$crystal = 8000000
'-----------------------------------
'Config Lcdpin = Pin , Db7 = portc.0 , Db6 = portc.1 , Db5 = portc.2 , Db4 = portc.3 , E = portc.4 , Rs = portc.5
'Config Lcd = 16 * 2
'Cursor Off
'Lcd "Time Setting:"
'Waitms 500
'Cls
'-----------------------------------
Config Debounce = 30
Config Clock = Soft

Enable Interrupts
Time$ = "12:35:00"


Config Portb = Output
Config Portd = Output

Config Portc = Output

Config Pina.6 = Input
Config Pina.7 = Input

'-----------------------------
Declare Sub Davazdah
Declare Sub Yek
Declare Sub Doo
Declare Sub See
Declare Sub Chahar
Declare Sub Panj
Declare Sub Shesh
Declare Sub Haft
Declare Sub Hasht
Declare Sub Noh
Declare Sub Dah
Declare Sub Yazdah
'-----------------------------
Declare Sub Vapanjdaghighe
Declare Sub Vadahdaghighe
Declare Sub Varob
Declare Sub Vabistdaghighe
Declare Sub Vabistopanjdaghighe
Declare Sub Vanim
Declare Sub Vasiopanjdaghighe
Declare Sub Bistkam
Declare Sub Robkam
Declare Sub Dahkam
Declare Sub Panjkam
Declare Sub Sefr
'-----------------------------
Dim Flag1 As Boolean
'-------------------------------------------------------
Dim Flagmin As Boolean
Dim Flagsaniye As Boolean

'------------------------------------------------------
Flag1 = 0
Flagmin = 0
Flagsaniye = 0
Do
'-------------------- hours -----------------
If _hour = 13 Then
_hour = 01
End If

If _hour = 12 Then
Call Davazdah
End If

If _hour = 01 Then
Call Yek
End If

If _hour = 02 Then
Call Doo
End If

If _hour = 03 Then
Call See
End If

If _hour = 04 Then
Call Chahar
End If

If _hour = 05 Then
Call Panj
End If

If _hour = 06 Then
Call Shesh
End If

If _hour = 07 Then
Call Haft
End If

If _hour = 08 Then
Call Hasht
End If

If _hour = 09 Then
Call Noh
End If

If _hour = 10 Then
Call Dah
End If

If _hour = 11 Then
Call Yazdah
End If
'-------------------------------

If _min = 01 Then
   If Flagmin = 1 Then
      _min = 00
      Flagmin = 0
   End If
End If

If _min = 59 Then
   If _sec = 59 Then
      If Flagsaniye = 1 Then
      _sec = 58
      Flagsaniye = 0
      End If

   End If

   'Decr _hour
      _min = 00
      Call Sefr
   End If


If _min = 05 Then
Call Vapanjdaghighe
Flagmin = 1
Flagsaniye = 1
End If

If _min = 10 Then
Call Vadahdaghighe
End If

If _min = 15 Then
Call Varob
End If

If _min = 20 Then
Call Vabistdaghighe
End If

If _min = 25 Then
Call Vabistopanjdaghighe
End If

If _min = 30 Then
Call Vanim
End If

If _min = 35 Then
Call Vasiopanjdaghighe
End If

If _min = 40 Then
   If Flag1 = 0 Then
   Incr _hour
   Flag1 = 1
   End If

Call Bistkam
End If

If _min = 45 Then
Flag1 = 0
Call Robkam
End If

If _min = 50 Then
Call Dahkam
End If

If _min = 55 Then
Call Panjkam
End If

If Pina.6 = 1 Then
_min = _min + 1
Waitms 50
   If _min = 60 Then
      _min = 00
      Call Sefr
 '     _hour = _hour + 1
   End If
End If

If Pina.7 = 1 Then
Incr _hour
Waitms 50
   If _hour = 13 Then
   _hour = 1
   End If
End If

Loop



Sub Davazdah
Set Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Yek
Reset Portb.0
Set Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Doo
Reset Portb.0
Reset Portb.1
Set Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub See
Reset Portb.0
Reset Portb.1
Reset Portb.2
Set Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Chahar
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Set Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Panj
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Set Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Shesh
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Set Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Haft
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Set Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Hasht
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Set Portd.0
Reset Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Noh
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Set Portd.1
Reset Portd.2
Reset Portd.3
End Sub

Sub Dah
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Set Portd.2
Reset Portd.3
End Sub

Sub Yazdah
Reset Portb.0
Reset Portb.1
Reset Portb.2
Reset Portb.3
Reset Portb.4
Reset Portb.5
Reset Portb.6
Reset Portb.7
Reset Portd.0
Reset Portd.1
Reset Portd.2
Set Portd.3
End Sub

Sub Vapanjdaghighe
Set Portd.4
Reset Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Set portc.3
Set portc.4
Reset portc.5
End Sub

Sub Vadahdaghighe
Set Portd.4
Set Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Set portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Varob
Set Portd.4
Reset Portd.5
Set Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Vabistdaghighe
Set Portd.4
Reset Portd.5
Reset Portd.6
Set Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Set portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Vabistopanjdaghighe
Set Portd.4
Reset Portd.5
Reset Portd.6
Set Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Set portc.3
Set portc.4
Set portc.5
End Sub

Sub Vanim
Set Portd.4
Reset Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Set portc.1
Reset portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Vasiopanjdaghighe
Set Portd.4
Reset Portd.5
Reset Portd.6
Reset Portd.7
Set portc.0
Reset portc.1
Reset portc.2
Set portc.3
Set portc.4
Set portc.5
End Sub

Sub Bistkam
Reset Portd.4
Reset Portd.5
Reset Portd.6
Set Portd.7
Reset portc.0
Reset portc.1
Set portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Robkam
Reset Portd.4
Reset Portd.5
Set Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Set portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Dahkam
Reset Portd.4
Set Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Set portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub

Sub Panjkam
Reset Portd.4
Reset Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Set portc.2
Reset portc.3
Set portc.4
Reset portc.5
End Sub

Sub Sefr
Reset Portd.4
Reset Portd.5
Reset Portd.6
Reset Portd.7
Reset portc.0
Reset portc.1
Reset portc.2
Reset portc.3
Reset portc.4
Reset portc.5
End Sub
