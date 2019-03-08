---
title: Parámetros
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 0652fe6076899020050d94378649018721b4b188
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147235"
---
# <a name="parameters"></a>Parámetros

Los argumentos son los nombres de los valores pasados a una función por una llamada de función. Los parámetros son los valores que la función espera recibir. En un prototipo de función, los paréntesis detrás del nombre de la función contienen una lista completa de los parámetros de la función y de sus tipos. Las declaraciones de parámetros especifican los tipos, tamaños e identificadores de los valores almacenados en los parámetros.

## <a name="syntax"></a>Sintaxis

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* es específico de Microsoft \*/

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* Un declarador de función \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)** /\* Declarador de nuevo estilo \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)** /\* Declarador de estilo obsoleto \*/

*parameter-type-list*: /\* La lista de parámetros \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

*parameter-type-list* es una secuencia de declaraciones de parámetros separadas por comas. La forma de cada parámetro en una lista de parámetros tiene el siguiente aspecto:

```C
[register]  type-specifier [declarator]
```

Los parámetros de función declarados con el atributo **auto** generan errores. Los identificadores de los parámetros se utilizan en el cuerpo de la función para hacer referencia a los valores pasados a la función. Puede asignar nombres a los parámetros de un prototipo, pero los nombres salen del ámbito al final de la declaración. Por lo tanto, los nombres de parámetro se pueden asignar de la misma manera o de manera diferente en la definición de función. Estos identificadores no se pueden volver a definir en el bloque extremo del cuerpo de la función, pero se pueden volver a definir en bloques anidados internos como si la lista de parámetros formara un bloque de inclusión.

Cada identificador de *parameter-type-list* debe ir precedido de su especificador de tipo adecuado, como se muestra en este ejemplo:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Si aparece al menos un parámetro en la lista de parámetros, la lista puede finalizar con una coma seguida de tres puntos (**, ...**). Esta construcción, denominada "notación de puntos suspensivos", indica un número variable de argumentos a la función. (Vea [Llamadas con un número variable de argumentos](../c-language/calls-with-a-variable-number-of-arguments.md) para obtener más información). Sin embargo, una llamada a la función debe tener como mínimo tantos argumentos como parámetros haya antes de la última coma.

Si no se van a pasar argumentos a la función, la lista de parámetros se sustituye por la palabra clave `void`. Este uso de `void` es distinto de su uso como especificador de tipo.

El orden y el tipo de los parámetros, incluido el uso de la notación de puntos suspensivos, deben ser iguales en todas las declaraciones de función (si existen) y en la definición de función. Los tipos de los argumentos después de conversiones aritméticas usuales deben ser compatibles en cuanto a asignación con los tipos de los parámetros correspondientes. (Vea [Conversiones aritméticas usuales](../c-language/usual-arithmetic-conversions.md) para obtener información sobre las conversiones aritméticas). Los argumentos que siguen a los puntos suspensivos no se comprueban. Un parámetro puede tener cualquier tipo fundamental, de estructura, de unión, de puntero o de matriz.

El compilador realiza las conversiones aritméticas usuales independientemente en cada parámetro y en cada argumento, si es necesario. Después de la conversión, ningún parámetro es más corto que `int` y ningún parámetro tiene el tipo **float**, a menos que el tipo de parámetro se especifique de forma explícita como **float** en el prototipo. Esto significa, por ejemplo, que la declaración de un parámetro como `char` tiene el mismo efecto que su declaración como `int`.

## <a name="see-also"></a>Vea también

[Definiciones de función de C](../c-language/c-function-definitions.md)
