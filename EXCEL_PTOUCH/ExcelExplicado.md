# Excel explicado
### ¿Que es lo que hace cada subrutina?

El Excel se encuentra documentado con la misma información que se detalla a continuación


#### La siguiente función es la que ejecuta la impresión de la etiqueta:

        Private Sub CommandButton1_Click()

        ' Esta es la función que hace la llamada al fichero de comandos externo
        '
        ' El programa que se usa es PPTTS.EXE (Print P-Touch Template on Shared printer)
        '
        ' Hay que tener en cuenta la carpeta en que se ecuentra el fichero de comandos

        ' Los datos que se envían posicionales son:
        '
        ' Posición 1 - Código de Torres
        ' Posición 2 - Fecha en formato YYMMD
        ' Posición 3 - Código de Cliente
        ' Posición 4 - Número de orden
        ' Posición 4 - Datos QR: Concatenación de los 4 datos anteriores

        
        Shell "c:\cmds\torres\pptts.exe localhost\QLCOMPARTIDA 6 1 " & _
                        "117680 " & _
                        Format(Range("C4"), "YYMMDD") & " " & _
                        Range("C5") & " " & _
                        Range("C6") & " " & _
                        "117680" & _
                        Format(Range("C4"), "YYMMDD") & _
                        Range("C5") & _
                        Range("C6") _
                , vbNormalFocus

        End Sub



#### La siguiente función controla el evento SelectionChange de la hoja y se aprovecha para facilitar al usuario el trabajo con la hoja de Excel:

        Private Sub Worksheet_SelectionChange(ByVal Target As Range)

        ' El evento Worksheet_SelectionChange se lanza cuando se pincha con el ratón en
        ' una celda distinta a la que se encuentra el cursor o cuando se selecciona un rango
        '
        ' Aprovechamos este evento para detectar cuando un usuario pincha en una zona
        ' de la hoja que contiene datos que pueden modificar el contenido de la etiqueta


        If Not Intersect(Range("f4:g21"), Target) Is Nothing Then
                
        ' Si el usuario pincha en el rango donde se ecuentran los clientes o sus códigos
        ' se actualiza el valor del código de cliente en la celda prevista a tal efecto
                
                Range("C5") = Range("F" & ActiveCell.Row)
        End If


        If Not Intersect(Range("I4:I12"), Target) Is Nothing Then
                
        ' Si el usuario pincha en el rango donde se ecuentra el número de orden
        ' se actualiza el valor del orden en la celda prevista a tal efecto
                
                Range("C6") = Range("I" & ActiveCell.Row)
        End If

        If Not Intersect(Range("L4:M12"), Target) Is Nothing Then
                                
        ' Si el usuario pincha en el rango donde se ecuentran las fecchas
        ' se actualiza el valor de la fecha en la celda prevista a tal efecto
                
                Range("C4") = Range("L" & ActiveCell.Row)
        End If

        If Not Intersect(Range("L3:M3"), Target) Is Nothing Then
                
        ' Si el usuario pincha en la cabecera de la tabla de fechas
        ' se actualiza el valor de la fecha referencia con la del día actual
                                
                Range("L12") = Now
        End If

        If Not Intersect(Range("K12:K12"), Target) Is Nothing Then
                
        ' Si el usuario pincha en la celda de retrasar una semana la fecha de referencia
        ' se actualiza el valor de la fecha referencia con la del día de referneica - 7 días
                                
                Range("L12") = Range("L12") - 7
                Range("L12").Select
        End If

        If Not Intersect(Range("N12:N12"), Target) Is Nothing Then
                
        ' Si el usuario pincha en la celda de adelantar una semana la fecha de referencia
        ' se actualiza el valor de la fecha referencia con la del día de referneica + 7 días
                                
                Range("L12") = Range("L12") + 7
                Range("L12").Select
        End If


        End Sub


