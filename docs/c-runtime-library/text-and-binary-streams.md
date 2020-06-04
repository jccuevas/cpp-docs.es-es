---
title: Secuencias binarias y de texto
ms.date: 11/04/2016
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 3754a62fa02bc532eb71eba6b0a8837791b179ea
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747714"
---
# <a name="text-and-binary-streams"></a>Secuencias binarias y de texto

Una secuencia de texto está formada por una o varias líneas de texto que se pueden escribir en una presentación de texto para que pueda leerlas. Al leer de una secuencia de texto, el programa lee un valor `NL` (nueva línea) al final de cada línea. Al escribir en una secuencia de texto, el programa escribe un valor `NL` para señalar el final de una línea. Para hacer coincidir las distintas convenciones entre entornos de destino para representar texto en archivos, las funciones de biblioteca pueden modificar el número y la representación de caracteres que se transmiten entre el programa y una secuencia de texto.

Por lo tanto, el posicionamiento dentro de una secuencia de texto está limitado. Puede obtener el indicador de posición de archivo actual mediante una llamada a [fgetpos](../c-runtime-library/reference/fgetpos.md) o [ftell](../c-runtime-library/reference/ftell-ftelli64.md). Puede colocar una secuencia de texto en una posición obtenida de este modo, o al principio o al final de la secuencia, mediante una llamada a [fsetpos](../c-runtime-library/reference/fsetpos.md) o [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Cualquier otro cambio de posición podría no ser compatible.

Para la máxima portabilidad, el programa no debe escribir:

- Archivos vacíos.

- Caracteres de espacio al final de una línea.

- Líneas parciales (omitiendo `NL` al final de un archivo).

- Caracteres distintos de los caracteres imprimibles, NL y `HT` (tabulación horizontal).

Si sigue estas reglas, la secuencia de caracteres que se leen desde una secuencia de texto (ya sea como bytes o caracteres multibyte) coincidirá con la secuencia de caracteres que se escribió en la secuencia de texto cuando se creó el archivo. De lo contrario, las funciones de biblioteca pueden quitar un archivo creado si el archivo está vacío cuando lo cierra. O bien, pueden modificar o eliminar caracteres escritos en el archivo.

Una secuencia binaria consta de uno o varios bytes de información arbitraria. Puede escribir el valor almacenado en un objeto arbitrario en una secuencia binaria (orientada a bytes) y leer exactamente lo que estaba almacenado en el objeto al escribirla. Las funciones de biblioteca no modifican los bytes que se transmiten entre el programa y una secuencia binaria. Sin embargo, pueden anexar un número arbitrario de bytes nulos en el archivo que se escribe con una secuencia binaria. El programa debe procesar estos bytes nulos adicionales al final de cualquier secuencia binaria.

Por lo tanto, el posicionamiento dentro de una secuencia binaria está bien definido, excepto el posicionamiento en relación con el final de la secuencia. Puede obtener y modificar el indicador de posición de archivo actual de la misma forma que en el caso de la secuencia de texto. Además, los desplazamientos usados por [ftell](../c-runtime-library/reference/ftell-ftelli64.md) y [fseek](../c-runtime-library/reference/fseek-fseeki64.md) cuentan bytes desde el principio de la secuencia (que es cero bytes), por lo que la aritmética de los enteros en estos desplazamientos ofrece resultados de predicción.

Una secuencia de bytes trata un archivo como una secuencia de bytes. En el programa, la secuencia es similar a la misma secuencia de bytes, excepto las posibles modificaciones que se han descrito anteriormente.

## <a name="see-also"></a>Vea también

[Archivos y secuencias](../c-runtime-library/files-and-streams.md)
