---
title: "Representaci&#243;n IEE de punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "double (tipo de datos), representación de punto flotante"
  - "float (palabra clave)"
  - "números de punto flotante, representación de IEEE"
  - "representación de punto flotante de IEEE"
  - "long double"
  - "real*10 (valor)"
  - "real*4 (valor)"
  - "real*8 (valor)"
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Representaci&#243;n IEE de punto flotante
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ es coherente con los estándares numéricos de IEEE.  Hay tres variedades internas de números reales.  En Visual C\+\+ se utilizan real\*4 y real\*8.  Real\*4 se declara con la palabra **float**.  Real\*8 se declara con la palabra **double**.  En programación para Windows de 32 bits, se asigna el tipo de datos `long double` al tipo **double**.  Sin embargo, se ofrece compatibilidad con el lenguaje de ensamblado para cálculos que utilicen el tipo de datos real\*10.  
  
 Los valores se almacenan del siguiente modo:  
  
|Valor|Se almacena como un|  
|-----------|-------------------------|  
|real\*4|bit de signo, exponente de 8 bits, mantisa de 23 bits|  
|real\*8|bit de signo, exponente de 11 bits, mantisa de 52 bits|  
|real\*10|bit de signo, exponente de 15 bits, mantisa de 64 bits|  
  
 En los formatos real\*4 y real\*8, se supone que hay un 1 inicial en la mantisa que no se almacena en la memoria, por lo que las mantisas son en realidad de 24 ó 53 bits, aunque sólo se almacenen 23 ó 52 bits.  El formato real\*10 almacena este bit.  
  
 Los exponentes se sesgan a la mitad de su valor posible.  Esto significa que debe restar este sesgo del exponente almacenado para obtener el exponente real.  Si el exponente almacenado es menor que el sesgo, se tratará en realidad de un exponente negativo.  
  
 Los exponentes se sesgan de la forma siguiente:  
  
|Exponente|Sesgado en|  
|---------------|----------------|  
|8 bits \(real\*4\)|127|  
|11 bits \(real\*8\)|1023|  
|15 bits \(real\*10\)|16383|  
  
 Estos exponentes no son potencias de diez, sino potencias de dos.  Es decir, con 8 bits se pueden almacenar hasta 127 exponentes.  El valor 2\*\*127 es del mismo orden de magnitud que 10\*\*38, el cual constituye el límite del formato real\*4.  
  
 La mantisa se almacena como una fracción binaria con la forma 1,XXX... .  Esta fracción tiene un valor mayor o igual que 1 y menor que 2.  Observe que los números reales se almacenan siempre en forma normalizada; es decir, la mantisa se desplaza hacia la izquierda de modo que el bit de orden superior de la mantisa sea siempre 1.  Como ese bit siempre va a ser 1, en los formatos real\*4 y real\*8 se supone y, por tanto, no se almacenan.  Se supone que el punto binario \(no el decimal\) está a la derecha del 1 inicial.  
  
 Por tanto, el formato para los distintos tamaños será el siguiente:  
  
|Formato|Byte 1|Byte 2|Byte 3|Byte 4|...|Byte n|  
|-------------|------------|------------|------------|------------|---------|------------|  
|real\*4|`SXXX XXXX`|`XMMM MMMM`|`MMMM MMMM`|`MMMM MMMM`|||  
|real\*8|`SXXX XXXX`|`XXXX MMMM`|`MMMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
|real\*10|`SXXX XXXX`|`XXXX XXXX`|`1MMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
  
 `S` representa el bit de signo, los valores `X` son los bits de exponente y los valores `M` son los bits de mantisa.  Tenga en cuenta que se supone que el primer bit de la izquierda tiene el formato real\*4 o real\*8, pero está presente como "1" en BYTE 3 del formato real\*10.  
  
 Para desplazar correctamente el punto binario, primero debe eliminar el sesgo del exponente y después mover el punto binario a la derecha o a la izquierda el número apropiado de bits.  
  
## Ejemplos  
 A continuación se muestran algunos ejemplos en formato real\*4:  
  
-   En el siguiente ejemplo, el valor del bit de signo es cero y el exponente almacenado es 128, o 100 0000 0 en binario, que equivale a 127 más 1.  La mantisa almacenada es \(1.\) 000 0000... 0000 0000, que tiene un 1 implícito inicial y un punto binario, por lo que el valor real de la mantisa es 1.  
  
    ```  
                        SXXX XXXX XMMM MMMM ... MMMM MMMM  
    2   =  1  * 2**1  = 0100 0000 0000 0000 ... 0000 0000 = 4000 0000  
    ```  
  
-   Igual que \+2, con la diferencia de que el bit de signo está establecido.  Esto es verdadero para todos los números de punto flotante en formato IEEE.  
  
    ```  
    -2  = -1  * 2**1  = 1100 0000 0000 0000 ... 0000 0000 = C000 0000  
    ```  
  
-   La misma mantisa, con el exponente aumentado en uno \(el valor sesgado es 129, o 100 0000 1 en binario.  
  
    ```  
    4  =  1  * 2**2  = 0100 0000 1000 0000 ... 0000 0000 = 4080 0000  
    ```  
  
-   El mismo exponente, con la mantisa una mitad mayor — es \(1.\) 100 0000 ...0000 0000, la cual, como es una fracción binaria, es 1 1\/2 \(los valores de los dígitos fraccionarios son 1\/2, 1\/4, 1\/8, etc.\).  
  
    ```  
    6  = 1.5 * 2**2  = 0100 0000 1100 0000 ... 0000 0000 = 40C0 0000  
    ```  
  
-   El mismo exponente que otras potencias de dos; la mantisa es uno menos que dos elevado a 127, o 011 1111 1 en binario.  
  
    ```  
    1  = 1   * 2**0  = 0011 1111 1000 0000 ... 0000 0000 = 3F80 0000  
    ```  
  
-   El exponente sesgado es 126 \(011 1111 0 en binario\) y la mantisa es \(1.\) 100 0000 ... 0000 0000, es decir, 1 1\/2.  
  
    ```  
    .75 = 1.5 * 2**-1 = 0011 1111 0100 0000 ... 0000 0000 = 3F40 0000  
    ```  
  
-   Exactamente igual a dos, con la diferencia de que el bit que representa 1\/4 está establecido en la mantisa.  
  
    ```  
    2.5 = 1.25 * 2**1 = 0100 0000 0010 0000 ... 0000 0000 = 4020 0000  
    ```  
  
-   1\/10 es una fracción que se repite en binario.  La mantisa es una pequeña parte de 1,6, y el exponente sesgado indica que 1,6 debe dividirse por 16 \(011 1101 1 en binario, que equivale a 123 en decimal\).  El exponente real es 123 – 127 \= –4, lo cual significa que el factor por el que se debe multiplicar es 2\*\*–4 \= 1\/16.  Observe que la mantisa almacenada se redondea en el último bit \(en un intento por representar, de la forma más precisa posible, el número que no se puede representar\). \(La razón por la que 1\/10 y 1\/100 no se pueden representar exactamente en binario es similar a la razón por la que 1\/3 no se puede representar exactamente en decimal.\)  
  
    ```  
    0.1 = 1.6 * 2**-4 = 0011 1101 1100 1100 ... 1100 1101 = 3DCC CCCD  
    ```  
  
-   `0  = 1.0 * 2**-128 = all zeros--a special case.`  
  
## Vea también  
 [Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)