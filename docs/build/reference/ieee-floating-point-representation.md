---
title: "Representación de punto flotante de IEEE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17fae0cbb16208d5c7e7346f354f3501e4803d96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ieee-floating-point-representation"></a>Representación IEE de punto flotante
Microsoft Visual C++ es coherente con los estándares numéricos de IEEE. Existen tres variedades internas de números reales. Real\*4 y real\*8 se utilizan en Visual C++. Real\*4 se declara con la palabra **float**. Real\*8 se declara con la palabra **doble**. En la programación de Windows de 32 bits, el `long double` se asigna al tipo de datos **doble**. Sin embargo, hay compatibilidad de lenguaje de ensamblado para cálculos que utilicen real * tipo de datos de 10.  
  
 Los valores se almacenan como sigue:  
  
|Valor|Almacenados como|  
|-----------|---------------|  
|real * 4|iniciar sesión bit, exponente de 8 bits, mantisa de 23 bits|  
|real * 8|iniciar sesión bit, exponentes de 11 bits, mantisa de 52 bits|  
|real * 10|iniciar sesión bit, exponente de 15 bits, mantisa de 64 bits|  
  
 Real * 4 y real\*8 formatos, hay un 1 inicial asumido en la mantisa que no se almacena en memoria, por lo que las mantisas son realmente 24 o 53 bits, aunque se almacenan solo 23 ó 52 bits. Real\*formato 10 almacena este bit.  
  
 Los exponentes se sesgan a la mitad de su valor posible. Esto significa que restar este sesgo del exponente almacenado para obtener al exponente real. Si el exponente almacenado es menor que la diferencia, es realmente un exponente negativo.  
  
 Los exponentes se sesgan como sigue:  
  
|Exponente|Inclina por|  
|--------------|---------------|  
|8 bits (real * 4)|127|  
|11 bits (real * 8)|1023|  
|15 bits (real * 10)|16383|  
  
 Estos exponentes no son potencias de diez; únicamente son potencias de dos. Es decir, los exponentes de 8 bits almacenados pueden ser hasta 127. El valor 2 ** 127 es aproximadamente equivalente al 10\*\*38, que es el límite real de real\*4.  
  
 La mantisa se almacena como una fracción binaria de la forma 1, xxx.... Esta fracción tiene un valor mayor o igual que 1 y menor que 2. Tenga en cuenta que los números reales se almacenan siempre en forma normalizada; es decir, la mantisa se desplaza hacia la izquierda forma que el bit de orden superior de la mantisa siempre es 1. Dado que este bit siempre es 1, se supone (no se almacenan) en real * 4 y real\*8 formatos. Se supone que el punto binario (no el decimal) justo a la derecha del 1 inicial.  
  
 El formato, a continuación, para los distintos tamaños es como sigue:  
  
|Formato|BYTES 1|BYTES 2|BYTES 3|BYTES 4|...|N bytes|  
|------------|------------|------------|------------|------------|---------|------------|  
|real * 4|`SXXX XXXX`|`XMMM MMMM`|`MMMM MMMM`|`MMMM MMMM`|||  
|real * 8|`SXXX XXXX`|`XXXX MMMM`|`MMMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
|real * 10|`SXXX XXXX`|`XXXX XXXX`|`1MMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
  
 `S`representa el bit de signo, el `X`de los bits de exponente y el `M`de los bits de mantisa. Tenga en cuenta que se supone que el bit situado real * 4 y real\*8 da formato, pero está presente como "1" en BYTE 3 del número real\*formato 10.  
  
 Para cambiar correctamente el punto binario, primero debe eliminar el sesgo del exponente y, a continuación, mover el punto binario a la derecha o izquierda el número apropiado de bits.  
  
## <a name="examples"></a>Ejemplos  
 Los siguientes son algunos ejemplos de real * 4 formato:  
  
-   En el ejemplo siguiente, el bit de signo es cero y el exponente almacenado es 128, o 100 0000 0 en binario, que equivale a 127 más 1. La mantisa almacenada es (1). 000 0000 ... 0000 0000, que tiene un implícito punto de 1 y binary inicial, por lo que la mantisa real es uno.  
  
    ```  
                        SXXX XXXX XMMM MMMM ... MMMM MMMM  
    2   =  1  * 2**1  = 0100 0000 0000 0000 ... 0000 0000 = 4000 0000  
    ```  
  
-   Igual que + 2, salvo que se establece el bit de signo. Esto es cierto para todos los números de punto flotante de formato IEEE.  
  
    ```  
    -2  = -1  * 2**1  = 1100 0000 0000 0000 ... 0000 0000 = C000 0000  
    ```  
  
-   La misma mantisa, exponente aumenta en uno (el valor sesgado es 129, o 100 0000 1 en binario.  
  
    ```  
    4  =  1  * 2**2  = 0100 0000 1000 0000 ... 0000 0000 = 4080 0000  
    ```  
  
-   Mismo exponente, mantisa es mayor a la mitad:, (1). 100 0000... 0000 0000, que, puesto que es una fracción binaria, es 1 1/2 (los valores de los dígitos fraccionarios son 1/2, 1/4, 1/8 etc.).  
  
    ```  
    6  = 1.5 * 2**2  = 0100 0000 1100 0000 ... 0000 0000 = 40C0 0000  
    ```  
  
-   Mismo exponente que otras potencias de dos, mantisa es uno menos de dos a 127 o 011 1111 1 en binario.  
  
    ```  
    1  = 1   * 2**0  = 0011 1111 1000 0000 ... 0000 0000 = 3F80 0000  
    ```  
  
-   El exponente sesgado es 126, 011 1111 0 en binario y la mantisa es (1). 100 0000 ... 0000 0000, que es 1 1/2.  
  
    ```  
    .75 = 1.5 * 2**-1 = 0011 1111 0100 0000 ... 0000 0000 = 3F40 0000  
    ```  
  
-   Exactamente igual que dos excepción en que el bit que representa 1/4 está establecido en la mantisa.  
  
    ```  
    2.5 = 1.25 * 2**1 = 0100 0000 0010 0000 ... 0000 0000 = 4020 0000  
    ```  
  
-   1/10 es una fracción que se repite en binario. La mantisa es una pequeña parte de 1.6, y el exponente sesgado indica que 1,6 debe dividirse por 16 (está 011 1101 1 en binario, que equivale a 123 en decimal). El exponente real es 123-127 = - 4, lo que significa que el factor por el que se va a multiplicar es 2 ** -4 = 1/16. Tenga en cuenta que la mantisa almacenada se redondea al último bit, un intento para representar el número no se puede representar de forma más precisa posible. (La razón por la que 1/10 y 1/100 son exactamente no puede representar en formato binario es similar a la razón que sea exactamente no puede representar en formato decimal 1/3.)  
  
    ```  
    0.1 = 1.6 * 2**-4 = 0011 1101 1100 1100 ... 1100 1101 = 3DCC CCCD  
    ```  
  
-   `0  = 1.0 * 2**-128 = all zeros--a special case.`  
  
## <a name="see-also"></a>Vea también  
 [Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)