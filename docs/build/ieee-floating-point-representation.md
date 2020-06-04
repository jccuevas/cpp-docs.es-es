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
ms.openlocfilehash: bb8523256c05479b303dec66ca79caa28e7cda03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169817"
---
# <a name="ieee-floating-point-representation"></a>Representación IEE de punto flotante

Microsoft C++ (MSVC) es coherente con los estándares numéricos IEEE. El estándar IEEE-754 describe los formatos de punto flotante, una manera de representar números reales en el hardware. Hay al menos cinco formatos internos para los números de punto flotante que se pueden representar en el hardware de destino del compilador de MSVC, pero el compilador solo usa dos de ellos. Los formatos de *precisión sencilla* (4 bytes) y de *precisión doble* (8 bytes) se usan en MSVC. La precisión sencilla se declara mediante la palabra clave **float**. La precisión doble se declara mediante la palabra clave **double**. El estándar IEEE también especifica formatos de *precisión media* (2 bytes) y de *precisión cuádruple* (16 bytes), así como un formato de *precisión doble extendida* (10 bytes), que algunos compiladores de C y C++ implementan como tipo de datos **long double**. En el compilador de MSVC, el tipo de datos **long double** se trata como un tipo distinto, pero el tipo de almacenamiento se asigna a **double**. Sin embargo, hay compatibilidad intrínseca y de lenguaje de ensamblado para los cálculos que usan los otros formatos, incluido el formato de precisión doble extendida (10 bytes), si es compatible con el hardware.

Los valores se almacenan de la siguiente manera:

|Valor|Almacenado como|
|-----------|---------------|
|precisión sencilla|bit de signo, exponente de 8 bits, significando de 23 bits|
|precisión doble|bit de signo, exponente de 11 bits, significando de 52 bits|
|precisión doble extendida|bit de signo, exponente de 15 bits, significando de 64 bits|

En los formatos de precisión sencilla y de precisión doble, se presupone que hay un 1 inicial en la parte fraccionaria, denominado *significando* (también conocido como *mantisa*), que no se almacena en memoria, por lo que los significandos son en realidad de 24 o 53 bits, aunque solo se almacenan 23 o 52 bits. El formato de precisión doble extendida sí almacena este bit.

Los exponentes se sesgan por la mitad de su valor posible. Esto significa que debe restar este sesgo del exponente almacenado para obtener el exponente real. Si el exponente almacenado es menor que la diferencia, se trata de un exponente negativo.

Los exponentes se sesgan de la siguiente manera:

|Exponente|Sesgado por|
|--------------|---------------|
|8 bits (precisión sencilla)|127|
|11 bits (precisión doble)|1023|
|15 bits (precisión doble extendida)|16383|

Estos exponentes no son potencias de diez, son potencias de dos. Es decir, los exponentes almacenados de 8 bits pueden oscilar entre -127 y 127, almacenados como de 0 a 254. El valor 2<sup>127</sup> es aproximadamente equivalente a 10<sup>38</sup>, que es el límite real de la precisión sencilla.

El significando se almacena como una fracción binaria con el formato "1.XXX…". Esta fracción tiene un valor igual o mayor que 1 y menor que 2. Tenga en cuenta que los números reales se almacenan siempre en *formato normalizado*; es decir, el significando se desplaza a la izquierda de modo que el bit de orden superior es siempre 1. Dado que este bit siempre es 1, se da por supuesto (no se almacena) en los formatos de precisión sencilla y de precisión doble. Se da por supuesto que el punto binario (no decimal) está justo a la derecha del 1 inicial.

Por lo tanto, el formato para los distintos tamaños es el siguiente:

|Formato|byte 1|byte 2|byte 3|byte 4|...|byte n|
|------------|------------|------------|------------|------------|---------|------------|
|precisión sencilla| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|precisión doble|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|precisión doble extendida|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` representa el bit de signo, las `X` son los bits del exponente sesgado y las `M` son los bits del significando. Tenga en cuenta que el bit más a la izquierda se da por supuesto en los formatos de precisión sencilla y precisión doble, pero está presente como "1" en el byte 3 del formato de precisión doble extendida.

Para desplazar el punto binario correctamente, primero debe quitar el sesgo del exponente y, a continuación, mover el punto binario a la derecha o a la izquierda el número de bits adecuado.

## <a name="special-values"></a>Valores especiales

Los formatos de punto flotante incluyen algunos valores que se tratan de forma especial.

### <a name="zero"></a>Cero

No se puede normalizar "cero", lo que hace que no se pueda representar en el formato normalizado de un valor de precisión simple o de precisión doble. Un patrón de bits especial de todo ceros representa 0. También es posible representar -0 como cero con el conjunto de bits de signo, pero -0 y 0 siempre se comparan como iguales.

### <a name="infinities"></a>Infinitos

Los valores +∞ y −∞ están representados por un exponente de todo unos y un significando de todo ceros. Tanto los infinitos positivos como los negativos se pueden representar mediante el bit de signo.

### <a name="subnormals"></a>Números no normales

Es posible representar números de magnitud menor que el número normalizado más pequeño. Estos números se conocen como números *no normales* o *desnormalizados*. Si los valores del exponente son todo ceros y el significando es distinto de cero, se considera que el bit inicial implícito del significando es cero, no uno. La precisión de los números desnormalizados disminuye a medida que aumenta el número de ceros iniciales en el significando.

### <a name="nan---not-a-number"></a>NaN (no es un número)

Es posible representar valores que no son un número real, como 0/0, en el formato de punto flotante de IEEE. Un valor de este tipo se denomina *NaN*. Un valor NaN se representa mediante un exponente de todo unos y un significando distinto de cero. Hay dos tipos de valores NaN: *simples* (o QNaN) y de *señalización* (o SNaN). Los NaN simples tienen un 1 inicial en el significando y, por lo general, se propagan a través de una expresión. Representan un valor indeterminado, como el resultado de la división por infinito o la multiplicación de un infinito por cero. Los NaN de señalización tienen un cero inicial en el significando. Se usan en las operaciones que no son válidas para señalar una excepción de hardware de punto flotante.

## <a name="examples"></a>Ejemplos

A continuación, se muestran algunos ejemplos del formato de precisión sencilla:

- Para el valor 2, el bit de signo es cero y el exponente almacenado es 128, o 1000 0000 en binario, que es 127 más 1. El significando binario almacenado es (1.) 000 0000 0000 0000 0000 0000, que tiene un 1 inicial implícito y un punto binario, por lo que el significando real es uno.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- El valor -2. Es igual que +2, excepto que se establece el bit de signo. Esto es así para todos los números de punto flotante con formato IEEE negativo.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- El valor 4. Es el mismo significando, pero el exponente aumenta en uno (el valor sesgado es 129 o 100 0000 1 en binario).

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- El valor 6. Presenta el mismo exponente, pero el significando es una mitad mayor, es (1.) 100 0000 … 0000 0000, por lo que, como se trata de una fracción binaria, es 1 1/2, ya que los valores de los dígitos fraccionarios son 1/2, 1/4, 1/8, etc.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |6|1.5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- El valor 1. Tiene el mismo significando que otras potencias de dos, pero el exponente sesgado es uno menos de dos en 127, o 011 1111 1 en binario.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- El valor 0,75. El exponente sesgado es 126, 011 1111 0 en formato binario, y el significando es (1.) 100 0000 … 0000 0000, que es 1 1/2.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.75|1.5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- El valor 2,5. Es exactamente igual que dos, salvo que el bit que representa 1/4 se establece en el significando.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2.5|1.25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 es una fracción repetida en formato binario. El significando es solo 1,6 y el exponente sesgado indica que 1,6 debe dividirse por 16 (es 011 1101 1 en formato binario, lo que equivale a 123 en formato decimal). El exponente real es 123 - 127 = -4, lo que significa que el factor por el que se va a multiplicar es 2<sup>-4</sup> = 1/16. Tenga en cuenta que el significando almacenado se redondea en el último bit en un intento de representar el número no representable de la manera más precisa posible. (La razón por la que 1/10 y 1/100 no se pueden representar de forma exacta en formato binario es similar a la razón por la que tampoco se puede representar 1/3 de forma exacta en formato decimal).

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Cero es un caso especial en el que se usa la fórmula para el mínimo valor positivo representable posible, que es todo ceros.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Vea también

[Por qué los números de punto flotante pierden precisión](why-floating-point-numbers-may-lose-precision.md)
