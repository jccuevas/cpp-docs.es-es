---
title: Tamaño de tipos y variables de ensamblado insertado
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: bc98c8561a7fd06f875781802558cdd7e71a67ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169245"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Tamaño de tipos y variables de ensamblado insertado

**Específicos de Microsoft**

Los operadores de **longitud**, **tamaño**y **tipo** tienen un significado limitado en el ensamblado alineado. No se pueden utilizar en absoluto con el operador `DUP` (porque no se puede definir datos con las directivas o los operadores de MASM). No obstante, puede utilizarlos para buscar el tamaño de variables o tipos de C o C++:

- El operador **length** puede devolver el número de elementos de una matriz. Devuelve el valor 1 para las variables que no son de matriz.

- El operador **size** puede devolver el tamaño de una variable C C++ o. El tamaño de una variable es el producto de su **longitud** y **tipo**.

- El operador **Type** puede devolver el tamaño de un C o C++ de un tipo o una variable. Si la variable es una matriz, **Type** devuelve el tamaño de un único elemento de la matriz.

Por ejemplo, si el programa tiene una matriz **int** de 8 elementos,

```cpp
int arr[8];
```

las siguientes expresiones de C y ensamblado producen el tamaño de `arr` y sus elementos.

|__asm|C|Size|
|-------------|-------|----------|
|**Longitud** ARR|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**Tamaño** ARR|`sizeof`(arr)|32|
|**Tipo** ARR|`sizeof`(arr[0])|4|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
