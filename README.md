# jinkama
openfile
#ce ----------------------------------------------------------------------------
#include <FileConstants.au3>
#include <MsgBoxConstants.au3>
#include <Array.au3>
#include <Misc.au3>

$aArrayComb = '0123456789'
$aArrayComb = StringSplit($aArrayComb, "")

Local Const $sFilePath = "C:\FileOpen.txt"

; Abrir O Arquivo
Local $hFileOpen = FileOpen($sFilePath, $FO_READ + $FO_OVERWRITE)

If $hFileOpen = -1 Then
   MsgBox($MB_SYSTEMMODAL, "", "There is not a previous point break.")
EndIf

HotKeySet("{ESC}", "Terminate")
$chave = ""

For $1 = 1 To $aArrayComb[0]
   For $2 = 1 To $aArrayComb[0]
      For $3 = 1 To $aArrayComb[0]
         $chave &= "Combination : " & $aArrayComb[$1] & $aArrayComb[$2] & $aArrayComb[$3] & "   Position : " & $1 & $2 & $3 & @CRLF
         Consolewrite($chave & @crlf)
      Next
   Next
Next

Func Terminate()
   $pos = $1 & $2 & $3
   FileWrite("C:\FileOpen.txt", $pos)
