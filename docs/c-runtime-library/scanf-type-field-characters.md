---
title: scanf (Caracteres de campo de tipo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50db1a8370a43b8b0c43c7c228c7b3acf9dd2c8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082890"
---
# <a name="scanf-type-field-characters"></a>scanf (Caracteres de campo de tipo)

La siguiente información se aplica a cualquiera de la familia de funciones `scanf` , incluidas las versiones seguras, como `scanf_s`.

El carácter de `type` es el único campo de formato necesario; aparece después de cualquier campo de formato opcional. El carácter de `type` determina si el argumento asociado se interpreta como un carácter, una cadena o un número.

### <a name="type-characters-for-scanf-functions"></a>Caracteres de tipo para las funciones scanf

|Carácter|Tipo de entrada esperada|Tipo de argumento|¿Argumento de tamaño en la versión segura?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Carácter. Cuando se usa con funciones `scanf` , especifica un carácter de un solo byte; cuando se usa con funciones `wscanf` , especifica un carácter ancho. Cuando se especifica `c` , se leen los caracteres de espacio en blanco que normalmente se omiten. Para leer el siguiente carácter de un solo byte que no sea un espacio en blanco, use `%1s`; para leer el siguiente carácter ancho que no sea un espacio en blanco, use `%1ws`.|Puntero a `char` cuando se utiliza con funciones `scanf` , puntero a `wchar_t` cuando se utiliza con funciones `wscanf` .|Obligatorio. El tamaño no incluye espacio para un terminador nulo.|
|`C`|Carácter de tamaño opuesto. Cuando se usa con funciones `scanf` , especifica un carácter ancho; cuando se usa con funciones `wscanf` , especifica un carácter de un solo byte. Cuando se especifica `C` , se leen los caracteres de espacio en blanco que normalmente se omiten. Para leer el siguiente carácter de un solo byte que no sea un espacio en blanco, use `%1s`; para leer el siguiente carácter ancho que no sea un espacio en blanco, use `%1ws`.|Puntero a `wchar_t` cuando se utiliza con funciones `scanf` , puntero a `char` cuando se utiliza con funciones `wscanf` .|Obligatorio. El argumento de tamaño no incluye espacio para un terminador nulo.|
|`d`|Entero decimal.|Puntero a `int`.|No.|
|`i`|Entero. Hexadecimal si la cadena de entrada comienza con “0x” o “0X”, octal si la cadena comienza con “0”, decimal en el resto de los casos.|Puntero a `int`.|No.|
|`o`|Entero octal.|Puntero a `int`.|No.|
|`p`|Dirección de puntero en dígitos hexadecimales. El número máximo de caracteres leídos depende del tamaño del puntero (32 o 64 bits), que depende de la arquitectura de la máquina. "0x" o "0X" se aceptan como prefijos.|Puntero a `void*`.|No.|
|`u`|Entero decimal sin signo.|Puntero a `unsigned int`.|No.|
|`x`|Entero hexadecimal.|Puntero a `int`.|No.|
|`e`, `E`, `f`, `F`, `g`, `G`|Valor de punto flotante que consta de un signo opcional (+ o -), una serie de uno o varios dígitos decimales que contiene el separador decimal y un exponente opcional ("e" o "E") seguido por un valor entero con signo opcional.|Puntero a `float`.|No.|
|`a`, `A`|Valor de punto flotante que consta de una serie de uno o varios dígitos hexadecimales que contiene un punto decimal opcional y un exponente ("p" o "P") seguido por un valor decimal.|Puntero a `float`.|No.|
|`n`|No lee ninguna entrada de secuencia o búfer.|Puntero a `int`, dentro del cual se almacena el número de caracteres correctamente leídos de la secuencia o búfer hasta ese punto en la llamada actual a funciones `scanf` o `wscanf` .|No.|
|`s`|Cadena, hasta el primer carácter de espacio en blanco (espacio, tabulación o nueva línea). Para leer cadenas no delimitadas por caracteres de espacio, use el conjunto de corchetes (`[ ]`), como se describe en [scanf Width Specification](../c-runtime-library/scanf-width-specification.md).|Cuando se usa con funciones `scanf` , especifica un carácter de un solo byte; cuando se usa con funciones `wscanf` , especifica una matriz de caracteres anchos. En cualquiera de los casos, la matriz de caracteres debe ser lo suficientemente grande como para que quepa el campo de entrada más el carácter nulo de terminación, que se anexa automáticamente.|Obligatorio. El tamaño incluye espacio para un terminador nulo.|
|`S`|Cadena de caracteres tamaño opuesto, hasta el primer carácter de espacio en blanco (espacio, tabulación o nueva línea). Para leer cadenas no delimitadas por caracteres de espacio, use un conjunto de corchetes (`[ ]`), tal y como se describe en [scanf (Especificación de ancho)](../c-runtime-library/scanf-width-specification.md).|Cuando se usa con funciones `scanf`, especifica una matriz de caracteres anchos; cuando se usa con funciones `wscanf`, especifica una matriz de caracteres de un solo byte. En cualquiera de los casos, la matriz de caracteres debe ser lo suficientemente grande como para que quepa el campo de entrada más el carácter nulo de terminación, que se anexa automáticamente.|Obligatorio. El tamaño incluye espacio para un terminador nulo.|


Los argumentos de tamaño, si son necesarios, deben pasarse a la lista de parámetros inmediatamente después del argumento al que se aplican. Por ejemplo, el código siguiente:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

lee una cadena con una longitud máxima de 10 en `string1`y una cadena con una longitud máxima de 8 en `string2`. Los tamaños de búfer deben ser al menos un carácter mayor que las especificaciones de ancho, ya que se debe reservar espacio para el terminador nulo.

La cadena de formato puede controlar una entrada de caracteres de byte único o anchos independientemente de si se utiliza la versión de carácter de byte único o de carácter ancho de la función. Por lo tanto, para leer caracteres de byte único o anchos con funciones `scanf` y `wscanf` , use especificadores de formato de la siguiente manera.

|Para leer caracteres como|Utilice esta función|Con estos especificadores de formato|
|--------------------------|-----------------------|----------------------------------|
|un solo byte|funciones`scanf` |`c`, `hc`o `hC`|
|un solo byte|funciones`wscanf` |`C`, `hc`o `hC`|
|anchos|funciones`wscanf` |`c`, `lc`o `lC`|
|anchos|funciones`scanf` |`C`, `lc`o `lC`|

Para analizar cadenas con funciones `scanf` y `wscanf` , utilice la tabla anterior con especificadores de tipo de formato `s` y `S` en lugar de `c` y `C`.

## <a name="see-also"></a>Vea también

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)