---
title: Representación de punto flotante de IEEE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61545d57a8a42f45616bd788defacaba12785971
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608246"
---
# <a name="ieee-floating-point-representation"></a>Representación IEE de punto flotante

Microsoft Visual C++ es coherente con los estándares numéricos IEEE. El estándar IEEE 754 describe los formatos de punto flotante, una forma de representar números reales en hardware. Hay al menos cinco formatos internos para números de punto flotante que se puede representables en la que apunta el compilador de MSVC de hardware, pero el compilador usa sólo dos de ellos. El *precisión sencilla* (4 bytes) y *doble precisión* formatos (8 bytes) que se usan en Visual C++. Precisión sencilla que se declara con la palabra clave **float**. Precisión doble que se declara con la palabra clave **doble**. También especifica el estándar IEEE *Media precisión* (2 bytes) y *cuádruplo precisión* formatos (16 bytes), así como un *doble precisión extendida* (10 bytes) formato, que algunos compiladores de C y C++ se implementan como el **long double** tipo de datos. En el compilador de Visual C++, el **long double** tipo de datos se trata como un tipo distinto, pero el tipo de almacenamiento se asigna a **doble**. Hay, sin embargo, intrínseca y soporte técnico de lenguaje de ensamblado para realizar cálculos con los demás formatos, incluido el formato de doble precisión extendida (10 bytes), donde el hardware lo admite.

Los valores se almacenan como sigue:

|Valor|Almacenados como|
|-----------|---------------|
|precisión simple|Inicie sesión bit, exponente de 8 bits, mantisa de 23 bits|
|precisión doble|Inicie sesión bit, exponentes de 11 bits, mantisa de 52 bits|
|doble precisión extendida|Inicie sesión bit, exponente de 15 bits y exponentes de 64 bits|

En los formatos de precisión sencilla y doble precisión, hay un 1 inicial asumido en la parte fraccionaria, llamada el *significandos* (y a veces se denomina el *mantisa*), que no se almacenan en memoria, por lo que los significandos son realmente 24 o 53 bits, aunque se almacenan solo 23 ó 52 bits. El formato de doble precisión extendida almacena realmente este bit.

Los exponentes están orientados a la mitad de su valor posible. Esto significa que restar este sesgo del exponente almacenado para obtener al exponente real. Si el exponente almacenado es menor que el valor de sesgo, es realmente un exponente negativo.

Los exponentes se sesgan como sigue:

|Exponente|Sesgados por|
|--------------|---------------|
|8 bits (precisión simple)|127|
|11 bits (precisión doble)|1023|
|15 bits (extendido de precisión doble)|16383|

Estos exponentes no son potencias de diez; son potencias de dos. Es decir, los exponentes de 8 bits almacenados pueden oscilar entre -127 y 127, almacenados como 0 a 254. El valor 2<sup>127</sup> es aproximadamente equivalente al 10<sup>38</sup>, que es el límite real de precisión sencilla.

La mantisa se almacena como una fracción binaria del formulario … 1, xxx. Esta fracción tiene un valor mayor o igual que 1 y menor que 2. Tenga en cuenta que los números reales se almacenan siempre en *normalizado formulario*; es decir, la mantisa se desplaza hacia la izquierda que el bit de orden superior de la mantisa siempre es 1. Dado que este bit siempre es 1, se supone (no almacenado) en los formatos de precisión sencilla y doble precisión. Se supone que el punto binario (no decimal) justo a la derecha del 1 inicial.

El formato, a continuación, para los distintos tamaños es como sigue:

|Formato|1 byte|2 bytes|3 bytes|4 bytes|...|n bytes|
|------------|------------|------------|------------|------------|---------|------------|
|precisión simple| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|precisión doble|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|doble precisión extendida|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` representa el bit de signo, el `X`del son los bits de exponente sesgados y la `M`del son los bits de mantisa. Tenga en cuenta que el bit situado en formatos de doble precisión y solo se asume, pero está presente como "1" en byte 3 del formato de doble precisión extendida.

Para cambiar correctamente el punto binario, primero debe eliminar el sesgo del exponente y, a continuación, mover el punto binario a la derecha o izquierda el número apropiado de bits.

## <a name="special-values"></a>Valores especiales

Los formatos de punto flotante incluyen algunos valores que se tratan de manera especial.

### <a name="zero"></a>Cero

No se puede normalizar cero, lo que hace que no se puede representar en la forma normalizada de un valor de precisión simple o doble precisión. Un patrón de bits especial de todos los ceros representa 0. También es posible para representar - conjunto de bits 0 como cero con el inicio de sesión, pero - 0 y 0 siempre se consideran iguales.

### <a name="infinities"></a>Infinitos

El + ∞ y −∞ valores se representan mediante un exponente de todos los y una mantisa de ceros. Infinitos positivos y negativos se pueden representar con el bit de signo.

### <a name="subnormals"></a>Subnormals

Es posible representar números de menor magnitud que el número más pequeño normalizado. Estos números se conocen como *subnormal* o *desnormalizado* números. Si el exponente es todo ceros y la mantisa es distinto de cero, se consideran implícita bits iniciales del significando sea cero, no uno. La precisión de números subnormal deja de funcionar como aumenta el número de ceros a la izquierda de la mantisa.

### <a name="nan---not-a-number"></a>NaN - no es un número

Es posible representar los valores que no son un número real, como 0 / 0, en el formato de punto flotante de IEEE. Un valor de esta clase se denomina un *NaN*. Un NaN se representa mediante un exponente de todos los y un significado distinto de cero. Hay dos tipos de NaNs, *quiet* NaN o QNaNs, y *señalización* NaN o SNaNs. NaN quiet tiene un líder en el significado y generalmente se propaga a través de una expresión. Representan un valor indeterminado, como el resultado de dividir por infinito o multiplicar infinity por cero. NaN de señalización tiene un cero inicial en la mantisa. Se usan para las operaciones que no son válidas, para indicar una excepción de punto flotante de hardware.

## <a name="examples"></a>Ejemplos

Estos son algunos ejemplos de formato de precisión sencilla:

- Para el valor 2, el bit de signo es cero y el exponente almacenado es 128 o 1000 0000 en formato binario, que es 127 más 1. La mantisa binaria almacenada es (1). 000 0000 0000 0000 0000 0000, que tiene un implícito inicial 1 y un punto binario, por lo que la mantisa real es uno.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- El valor -2. Igual que + 2, salvo que se establece el bit de signo. Esto es cierto para el valor negativo de todos los números de punto flotante de formato IEEE.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- El valor 4. Misma mantisa y exponente aumenta en uno (valor sesgado es 129, o 100 0000 1 en binario.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|1000 de 0000 0100 0000 0000 0000 0000 0000|0x40800000|

- El valor 6. Exponente mismo, la mantisa es mayor a la mitad, ello (1). 100 0000 ... 0000 0000, que, puesto que es una fracción binaria, es 1 1/2 porque los valores de los dígitos fraccionarios son 1/2, 1/4, 1/8 y así sucesivamente.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |6|2 * 1.5<sup>2</sup>|1100 de 0000 0100 0000 0000 0000 0000 0000|0x40C00000|

- El valor 1. Mismo significado que otras potencias de dos, el exponente sesgado es uno menos de dos a 127 o 011 1111 1 en binario.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- El valor de 0,75. El exponente sesgado es 126, 011 1111 0 en binario y la mantisa es (1). 100 0000 ... 0000 0000, que es 1 1/2.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.75|1,5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- El valor 2.5. Tal y como dos excepción en que el bit que representa 1/4 está establecido en la mantisa.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |2.5|2 * 1.25<sup>1</sup>|0010 de 0000 0100 0000 0000 0000 0000 0000|0x40200000|

- 1/10 es una fracción de repetición en formato binario. La mantisa es una pequeña parte de 1.6, y el exponente sesgado indica que 1,6 dividirse por 16 (es 011 1101 1 en binario, que es de 123 en formato decimal). El exponente real es 123-127 = - 4, lo que significa que el factor por el que se va a multiplicar 2<sup>-4</sup> = 1/16. Tenga en cuenta que la mantisa almacenada se redondea hacia arriba en la última sección, un intento para representar el número no se puede representar de forma más precisa posible. (La razón por la que 1/10 y 1/100 son exactamente no se puede representar en formato binario es similar a la razón que sea exactamente no se puede representar en formato decimal 1/3.)

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Cero es un caso especial que utiliza la fórmula para el valor mínimo posible que se puede representar positivo, que es todo ceros.

   |Valor|Fórmula|Representación binaria|Hexadecimal|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Vea también

[Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)