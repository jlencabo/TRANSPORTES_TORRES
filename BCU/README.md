# BARCODE UTILITY

## NORMALIZACIÓN

La normalización acordada para el nombrado de ficheros ha sido la siguiente:

  **CE-Oxxxxxx-Fxxxxxx-Cxxxxxxxxxxx.pdf**

El significado de cada una de las partes es el siguiente:

* CE - Conforme de Entrega
* Oxxxxxx - Operador. 6 dígitos justificados con ceros a la izquierda
* Fxxxxxx - Fecha. 6 dígitos que representan AAMMDD (AñoMesDia)
* Cxxxxxxxxxx - Cliente. 11 dígitos. Los 10 primeros dígitos es el código de cliente en SAP justificado con ceros a la izquierda. El último dígito es un número entre 1 y 9 que representa el número de entrega. Puede darse el caso de que un cliente tuviera mas de una entrega el mismo día. Se utiliza este último dígito para identifcarlo de modo único. Es responsabilidad de TORRES asignar este número en base a su operativa

Ejemplos: 

  **CE-O117680-F190620-C00000562711.pdf**

Conforme de entrega 1 al cliente 0000056271 por parte del operador 117680 el día 20 de Junio de 2019

  **CE-O117680-F190620-C00000562712.pdf**

Conforme de entrega 2 al cliente 0000056271 por parte del operador 117680 el día 20 de Junio de 2019

Los documentos se irán almacenando automáticamente en la carpeta compartida del departamento nombrada como "ConformesEntrega". 
