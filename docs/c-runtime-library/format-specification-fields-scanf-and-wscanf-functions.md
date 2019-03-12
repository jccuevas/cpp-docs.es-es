---
title: 'Campos de especificación de formato: funciones scanf y wscanf'
ms.date: 11/04/2016
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 5b45de9af3642825f1fddf3a1560b2fc1dbc4ffc
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748468"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Campos de especificación de formato: funciones scanf y wscanf

Esta información se aplica a toda la familia de funciones `scanf`, incluidas las versiones seguras, y describe los símbolos que se usan para indicar a las funciones `scanf` cómo analizar el flujo de entrada (por ejemplo, el flujo de entrada `stdin` para `scanf`) en los valores que se insertan en variables de programa.

Una especificación de formato tiene la forma siguiente:

`%`[`*`] [[width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)

El argumento `format` especifica la interpretación de la entrada y puede contener uno o varios de los siguientes elementos:

- Caracteres de espacio en blanco: en blanco (" "); tabulador ("\t"); o nueva línea ("\n"). Un carácter de espacio en blanco hace que `scanf` lea, pero no almacene, todos los caracteres de espacio en blanco consecutivos en la entrada hasta el siguiente carácter que no sea un espacio en blanco. Un solo carácter de espacio en blanco en el formato coincide con cualquier número (incluido el 0) y combinación de caracteres de espacio en blanco de la entrada.

- Caracteres que no sean espacios en blanco, excepto el signo de porcentaje (`%`). Un carácter que no sea un espacio en blanco hace que `scanf` lea, pero no almacene, un carácter que no sea un espacio en blanco coincidente. Si no coincide con el siguiente carácter del flujo de entrada, `scanf` finaliza.

- Especificaciones de formato, introducidas mediante el signo de porcentaje (`%`). Una especificación de formato hace que `scanf` lea y convierta los caracteres de la entrada en valores de un tipo especificado. El valor se asigna a un argumento de la lista de argumentos.

El formato se lee de izquierda a derecha. Se espera que los caracteres fuera de las especificaciones de formato coincidan con la secuencia de caracteres en el flujo de entrada; los caracteres coincidentes en el flujo de entrada se analizan pero no se almacenan. Si un carácter en el flujo de entrada está en conflicto con la especificación de formato, `scanf` finaliza y el carácter se queda en el flujo de entrada como si no se hubiera leído.

Cuando se encuentra la primera especificación de formato, el valor del primer campo de entrada se convierte de acuerdo con esta especificación y se almacena en la ubicación especificada por el primer `argument`. La segunda especificación de formato hace que el segundo campo de entrada se convierta y se almacene en el segundo `argument`, y así sucesivamente hasta el final de la cadena de formato.

Un campo de entrada se define como todos los caracteres hasta el primer carácter de espacio en blanco (espacio, tabulador o nueva línea), hasta el primer carácter que no se pueda convertir según la especificación de formato o hasta que se alcance el ancho de campo (si se especifica). Si hay demasiados argumentos para las especificaciones dadas, los argumentos adicionales se evalúan pero se omiten. Los resultados son impredecibles si no hay suficientes argumentos para la especificación de formato.

Cada campo de la especificación de formato es un único carácter o un número que indica una opción de formato en concreto. El carácter `type`, que aparece después del último campo opcional de formato, determina si el campo de entrada se interpreta como un carácter, una cadena o un número.

La especificación de formato más simple solo contiene el signo de porcentaje y un carácter `type` (por ejemplo `%s`). Si un signo de porcentaje (`%`) va seguido de un carácter que no tiene ningún significado como carácter de control de formato, ese carácter y los caracteres siguientes (hasta el siguiente signo de porcentaje) se tratan como una secuencia normal de caracteres, es decir, una secuencia de caracteres que debe coincidir con la entrada. Por ejemplo, para especificar que se introduzca un carácter de signo de porcentaje, use `%%`.

Un asterisco (`*`) después del signo de porcentaje suprime la asignación del campo de entrada siguiente, que se interpreta como un campo del tipo especificado. El campo se analiza pero no se almacena.

Las versiones seguras (las que tienen el sufijo `_s`) de la familia de funciones `scanf` requieren que se pase un parámetro de tamaño de búfer inmediatamente después de cada parámetro de tipo `c`, `C`, `s`, `S` o `[`. Para obtener más información sobre las versiones seguras de la familia de funciones `scanf`, consulte [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).

## <a name="see-also"></a>Vea también

[scanf (especificación de ancho)](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf (caracteres de campo de tipo)](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
