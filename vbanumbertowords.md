```vba
Function NumberToWords(ByVal MyNumber)
    Dim Units As String
    Dim Cents As String
    Dim DecimalPlace As Integer
    Dim Count As Integer
    Dim DecimalPart As String
    Dim WholePart As String
    
    Static Place(9) As String
    Place(2) = " Thousand "
    Place(3) = " Million "
    Place(4) = " Billion "
    Place(5) = " Trillion "

    ' Convert number to string and check for decimal
    MyNumber = Trim(CStr(MyNumber))
    DecimalPlace = InStr(MyNumber, ".")

    If DecimalPlace > 0 Then
        WholePart = Left(MyNumber, DecimalPlace - 1)
        DecimalPart = Mid(MyNumber, DecimalPlace + 1) & "00"
        DecimalPart = Left(DecimalPart, 2)
    Else
        WholePart = MyNumber
        DecimalPart = "00"
    End If

    Count = 1
    Do While WholePart <> ""
        Dim TempStr As String
        TempStr = ThreeDigitConversion(Right(WholePart, 3))
        If TempStr <> "" Then Units = TempStr & Place(Count) & Units
        If Len(WholePart) > 3 Then
            WholePart = Left(WholePart, Len(WholePart) - 3)
        Else
            WholePart = ""
        End If
        Count = Count + 1
    Loop

    ' Convert cents to words
    If DecimalPart = "00" Then
        Cents = " Pesos Only"
    Else
        Cents = " and " & ThreeDigitConversion(DecimalPart) & " Centavos Only"
    End If

    NumberToWords = Application.Trim(Units) & Cents
End Function

Private Function ThreeDigitConversion(ByVal Num As String) As String
    Dim Ones(9) As String
    Dim Teens(9) As String
    Dim Tens(9) As String
    
    Ones(1) = "One": Ones(2) = "Two": Ones(3) = "Three": Ones(4) = "Four"
    Ones(5) = "Five": Ones(6) = "Six": Ones(7) = "Seven": Ones(8) = "Eight": Ones(9) = "Nine"
    
    Teens(0) = "Ten": Teens(1) = "Eleven": Teens(2) = "Twelve": Teens(3) = "Thirteen"
    Teens(4) = "Fourteen": Teens(5) = "Fifteen": Teens(6) = "Sixteen"
    Teens(7) = "Seventeen": Teens(8) = "Eighteen": Teens(9) = "Nineteen"
    
    Tens(2) = "Twenty": Tens(3) = "Thirty": Tens(4) = "Forty"
    Tens(5) = "Fifty": Tens(6) = "Sixty": Tens(7) = "Seventy"
    Tens(8) = "Eighty": Tens(9) = "Ninety"

    Num = Right("000" & Num, 3)  ' Ensure three-digit format
    Dim Result As String

    ' Convert hundreds place
    If Mid(Num, 1, 1) <> "0" Then
        Result = Ones(Mid(Num, 1, 1)) & " Hundred "
    End If

    ' Convert tens place
    If Mid(Num, 2, 1) = "1" Then
        Result = Result & Teens(Mid(Num, 3, 1))
    Else
        If Mid(Num, 2, 1) <> "0" Then
            Result = Result & Tens(Mid(Num, 2, 1)) & " "
        End If
        If Mid(Num, 3, 1) <> "0" Then
            Result = Result & Ones(Mid(Num, 3, 1))
        End If
    End If

    ThreeDigitConversion = Trim(Result)
End Function
```