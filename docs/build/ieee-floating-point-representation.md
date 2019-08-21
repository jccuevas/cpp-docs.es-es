---
title: Representación IEE de punto flotante
ms.date: 05/06/2019
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
ms.openlocfilehash: de132dcf28747cd866229cff8972e2aed271a047
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630352"
---
# <a name="ieee-floating-point-representation"></a>Representación IEE de punto flotante

Microsoft C++ (MSVC) es coherente con los estándares numéricos de IEEE. El estándar IEEE-754 describe los formatos de punto flotante, una manera de representar números reales en el hardware. Hay al menos cinco formatos internos para los números de punto flotante que se pueden representar en el hardware de destino del compilador MSVC, pero el compilador solo usa dos de ellos. Los formatos de *precisión sencilla* (4 bytes) y *de doble precisión* (8 bytes) se usan en MSVC. La precisión sencilla se declara mediante la palabra clave **float**. La precisión doble se declara mediante la palabra clave **Double**. El estándar IEEE también especifica formatos *de media precisión* (2 bytes) y *cuádruple precisión* (16 bytes), así como un formato de *precisión doble* (10 bytes), que algunos de C y C++ compiladores implementan como el **largo** tipo de datos Double. En el compilador MSVC, el tipo de datos **Long Double** se trata como un tipo distinto, pero el tipo de almacenamiento se asigna a **Double**. Sin embargo, hay compatibilidad intrínseca y de lenguaje de ensamblado para los cálculos que usan los otros formatos, incluido el formato de precisión doble (10 bytes), donde es compatible con el hardware.

Los valores se almacenan de la siguiente manera:

|Value|Almacenado como|
|-----------|---------------|
|precisión sencilla|bit de signo, exponente de 8 bits, significado de 23 bits|
|precisión doble|bit de signo, exponente de 11 bits, significado de 52 bits|
|double-extended-precision|bit de signo, exponente de 15 bits, significado de 64 bits|

En los formatos de precisión sencilla y de doble precisión, se supone un 1 inicial en la parte fraccionaria, denominado significado (y a veces denominado *mantisa*), que no se almacena en la memoria, por lo que los significandos son realmente 24 o 53 bits, aunque solo se almacenan 23 o 52 bits. El formato de precisión doble extendida almacena realmente este bit.

Los exponentes se sesgan por la mitad de su valor posible. Esto significa que resta este sesgo del exponente almacenado para obtener el exponente real. Si el exponente almacenado es menor que la diferencia, en realidad es un exponente negativo.

Los exponentes se sesgan de la manera siguiente:

|Exponente|Sesgado por|
|--------------|---------------|
|8 bits (precisión sencilla)|127|
|11 bits (precisión doble)|1023|
|15 bits (precisión doble)|16383|

Estos exponentes no son potencias de diez; son potencias de dos. Es decir, los exponentes almacenados de 8 bits pueden oscilar entre-127 y 127, almacenados como 0 a 254. El valor 2<sup>127</sup> es aproximadamente equivalente a 10<sup>38</sup>, que es el límite real de precisión sencilla.

La mantisa se almacena como una fracción binaria con el formato 1.XXX.... Esta fracción tiene un valor mayor o igual que 1 y menor que 2. Tenga en cuenta que los números reales siempre se almacenan de *forma normalizada*; es decir, el significado se desplaza a la izquierda de modo que el bit de orden superior de la mantisa sea siempre 1. Dado que este bit siempre es 1, se supone (no se almacena) en los formatos de precisión sencilla y de precisión doble. Se supone que el punto binario (no decimal) está justo a la derecha del 1 de la izquierda.

El formato, a continuación, para los distintos tamaños es el siguiente:

|Formato|byte 1|byte 2|byte 3|byte 4|...|byte n|
|------------|------------|------------|------------|------------|---------|------------|
|precisión sencilla| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|precisión doble|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|double-extended-precision|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S`representa el bit de signo, `X`es el de los bits de exponente sesgado y `M`el de son los bits de significación. Tenga en cuenta que el bit más a la izquierda se presupone en los formatos de precisión sencilla y de doble precisión, pero está presente como "1" en byte 3 del formato de precisión doble.

Para desplazar el punto binario correctamente, primero debe dessesgar el exponente y, a continuación, mover el punto binario a la derecha o a la izquierda el número de bits adecuado.

## <a name="special-values"></a>Valores especiales

Los formatos de punto flotante incluyen algunos valores que se tratan de forma especial.

### <a name="zero"></a>Cero

No se puede normalizar cero, lo que hace que no se pueda representar en la forma normalizada de un valor de precisión simple o de precisión doble. Un patrón de bits especial de ceros representa 0. También es posible representar-0 como cero con el conjunto de bits de signo, pero-0 y 0 siempre se comparan como iguales.

### <a name="infinities"></a>Infinitos

Los valores + ∞ y − ∞ están representados por un exponente de todos y una mantisa de ceros. Tanto los infinitos positivos como los negativos se pueden representar mediante el bit de signo.

### <a name="subnormals"></a>Subnormalizaciones

Es posible representar números de magnitud menor que el número normalizado más pequeño. Estos números se conocen como números subnormales o desnormalizados. Si el exponente es todo ceros y el significado es distinto de cero, se considera que el bit inicial implícito del significado es cero, no uno. La precisión de los números subnormales deja de funcionar a medida que aumenta el número de ceros a la izquierda en la mantisa.

### <a name="nan---not-a-number"></a>NaN: no es un número

Es posible representar valores que no son un número real, como 0/0, en el formato de punto flotante de IEEE. Un valor de este tipo se denomina *Nan*. Un NaN se representa mediante un exponente de todos y un significado distinto de cero. Hay dos tipos de Nan, Nan *silencioso* o QNaNs, y Nan de *señalización* , o SNaNs. Los Nan no intermedios tienen un carácter inicial en el significado y, por lo general, se propagan a través de una expresión. Representan un valor indeterminado, como el resultado de la división por infinito o la multiplicación de un infinito por cero. los Nan de señalización tienen un cero inicial en el significado. Se utilizan para las operaciones que no son válidas para señalar una excepción de hardware de punto flotante.

## <a name="examples"></a>Ejemplos

A continuación se muestran algunos ejemplos del formato de precisión sencilla:

- Para el valor 2, el bit de signo es cero y el exponente almacenado es 128, o 1000 0000 en binario, que es 127 más 1. La mantisa binaria almacenada es (1). 000 0000 0000 0000 0000 0000, que tiene un punto inicial 1 y binario implícito, por lo que la mantisa real es una.

   |Value|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Valor-2. Igual que + 2, excepto que se establece el bit de signo. Esto es así para los números de punto flotante con formato IEEE negativo.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- El valor 4. La misma significa que el exponente aumenta en uno (el valor sesgado es 129 o 100 0000 1 en binario.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- El valor 6. El mismo exponente, el significado es mayor en la mitad, es (1). 100 0000 ... 0000 0000, que, como se trata de una fracción binaria, es 1 1/2 porque los valores de los dígitos fraccionarios son 1/2, 1/4, 1/8, etc.

   |Value|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |6|1,5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- El valor 1. La misma significa que otras potencias de dos, el exponente sesgado es uno menos de dos en 127 o 011 1111 1 en binario.

   |Value|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- El valor 0,75. El exponente sesgado es 126, 011 1111 0 en formato binario y el significado es (1). 100 0000 ... 0000 0000, que es 1 1/2.

   |Value|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.75|1,5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- El valor 2,5. Exactamente igual que dos, salvo que el bit que representa 1/4 se establece en el significado.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2.5|1,25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 es una fracción repetida en binaria. El significado es solo de 1,6 y el exponente sesgado indica que 1,6 se divide por 16 (es 011 1101 1 en binario, que es 123 en decimal). El exponente real es 123-127 =-4, lo que significa que el factor por el que se va a multiplicar es 2<sup>-4</sup> = 1/16. Tenga en cuenta que la mantisa almacenada se redondea en el último bit, un intento de representar el número no representable de la manera más precisa posible. (La razón por la que 1/10 y 1/100 no se pueden representar exactamente en formato binario es similar a la razón por la que 1/3 no se representará exactamente en formato decimal).

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.1|1,6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Cero es un caso especial en el que se usa la fórmula para el valor positivo representable mínimo posible, que es todo ceros.

   |Value|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Vea también

[Por qué los números de punto flotante pierden precisión](why-floating-point-numbers-may-lose-precision.md)