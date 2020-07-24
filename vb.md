


半形轉全形

'''
StrConv(string, conversion, LCID)
半形轉全形：vbWide
全形轉半形：vbNarrow
TT=StrConv("abcd123",vbWide)
==>TT="ａｂｃｄ１２３"
'''

20061226轉成日期方式2006/12/26
'''
CDate(Format(CInt(Me.TextBox1.Text), "0000/00/00"))
'''



把Excel內的Flash找出來另存的VBA程式碼
Excel內涵Flash，可是不知道為何無法撥放
```
    Dim tmpFileName As String, FileNumber As Integer
    Dim myFileId As Long
    Dim myArr() As Byte
    Dim i As Long
    Dim MyFileLen As Long, myIndex As Long
    Dim swfFileLen As Long
    Dim swfArr() As Byte
    
    tmpFileName = Application.GetOpenFilename("office File(*.doc;*.xls),*.doc;*.xls", , "確定要分析的 Office 檔")
    
    If tmpFileName = "False" Then Exit Sub
    myFileId = FreeFile
    Open tmpFileName For Binary As #myFileId
    MyFileLen = LOF(myFileId)
    ReDim myArr(MyFileLen - 1)
    Get myFileId, , myArr()
    Close myFileId
    Application.ScreenUpdating = False
    i = 0

    Do While i < MyFileLen
        If myArr(i) = &H46 Then
            If myArr(i + 1) = &H57 And myArr(i + 2) = &H53 Then
                swfFileLen = CLng(&H1000000) * myArr(i + 7) + CLng(&H10000) * myArr(i + 6) + CLng(&H100) * myArr(i + 5) + myArr(i + 4)
                ReDim swfArr(swfFileLen - 1)
                For myIndex = 0 To swfFileLen - 1
                    swfArr(myIndex) = myArr(i + myIndex)
                Next myIndex
                Exit Do
            Else
                i = i + 3
            End If
        Else
            i = i + 1
        End If
    Loop
    myFileId = FreeFile
    tmpFileName = Left(tmpFileName, Len(tmpFileName) - 4) & ".swf"
    Open tmpFileName For Binary As #myFileId
    Put #myFileId, , swfArr
    Close myFileId
    MsgBox "以" & tmpFileName & "名字保存"
    
End Sub
```



檢查字串是否有中文或全形字

```
Function ContainsChtString(str) As Boolean
    '檢查字串是否包含中文或全形字
    Dim i As Integer
    Dim Rc As Boolean
    Rc = False
    For i = 1 To Len(str)
        If Asc(Mid(str, i, 1)) < 0 Then
            Rc = True
            Exit For
        End If
    Next
    ContainsChtString = Rc
End Function
```

判斷Binary方式計算長度(LenB)與一般方式計算長度(Len)是否相同，如果不同就是有中文或全形!!
```
LenB(StrConv(myString, vbFromUnicode)) > Len(myString) 
```





```

```











```

```







```

```







```

```











```

```







```

```





```

```











```

```







```

```





