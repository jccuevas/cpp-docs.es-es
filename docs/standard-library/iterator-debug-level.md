---
title: _ITERATOR_DEBUG_LEVEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7219ed039e77d0857151c54e73a03a0d1f6a3f5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864143"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

La macro `_ITERATOR_DEBUG_LEVEL` controla si están habilitados los [iteradores comprobados](../standard-library/checked-iterators.md) y la [compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md). Esta macro reemplaza y combina la funcionalidad de las macros antiguas `_SECURE_SCL` y `_HAS_ITERATOR_DEBUGGING` .

## <a name="macro-values"></a>Valores de la macro

En la siguiente tabla se resumen los posibles valores de la macro `_ITERATOR_DEBUG_LEVEL`.

|Modo de compilación|Valor de la macro|Descripción|
|----------------------|----------------|-----------------|
|**Depuración**|||
||0|Deshabilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||1|Habilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||2 (predeterminado)|Habilita la depuración de iteradores. Los iteradores comprobados no son pertinentes.|
|**Release**|||
||0 (predeterminado)|Deshabilita los iteradores comprobados.|
||1|Habilita los iteradores comprobados. La depuración de iteradores no es pertinente.|

En modo de versión, el compilador genera un error si especifica `_ITERATOR_DEBUG_LEVEL` como 2.

## <a name="remarks"></a>Comentarios

La macro `_ITERATOR_DEBUG_LEVEL` controla si los [iteradores comprobados](../standard-library/checked-iterators.md) están habilitados y, en modo de depuración, si la [compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md) está habilitada. Si `_ITERATOR_DEBUG_LEVEL` está definido como 1 o 2, los iteradores comprobados garantizan que los límites de los contenedores no se han sobrescrito. Si `_ITERATOR_DEBUG_LEVEL` es 0, no se comprueban los iteradores. Cuando `_ITERATOR_DEBUG_LEVEL` está definido como 1, el uso no seguro de iteradores produce un error en tiempo de ejecución y el programa finaliza. Cuando `_ITERATOR_DEBUG_LEVEL` está definido como 2, el uso no seguro de iteradores produce una aserción y aparece un cuadro de diálogo de error en tiempo de ejecución que le permite interrumpir el depurador.

Dado que la macro `_ITERATOR_DEBUG_LEVEL` admite una funcionalidad similar a las macros `_SECURE_SCL` y `_HAS_ITERATOR_DEBUGGING`, es posible que no sepa qué macro y qué valor de macro usar en una situación determinada. Para evitar confusiones, se recomienda que use solo la macro `_ITERATOR_DEBUG_LEVEL`. En esta tabla se describe el valor de macro `_ITERATOR_DEBUG_LEVEL` equivalente que se usará para distintos valores de `_SECURE_SCL` y `_HAS_ITERATOR_DEBUGGING` en el código existente.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valor predeterminado de versión)|0 (deshabilitado)|0 (deshabilitado)|
|1|1 (habilitado)|0 (deshabilitado)|
|2 (valor predeterminado de depuración)|(no pertinente)|1 (habilitado en modo de depuración)|

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Ejemplo

Para especificar un valor para la macro `_ITERATOR_DEBUG_LEVEL`, use una opción del compilador [/D](../build/reference/d-preprocessor-definitions.md) para definirlo en la línea de comandos, o bien use `#define` antes de los encabezados de la biblioteca estándar de C++ incluidos en los archivos de código fuente. Por ejemplo, en la línea de comandos, para compilar *sample.cpp* en modo de depuración y usar la compatibilidad de los iteradores de depuración, puede especificar la definición de macro `_ITERATOR_DEBUG_LEVEL`:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

En un archivo de código fuente, especifique la macro antes de los encabezados de la biblioteca estándar que definen los iteradores.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Vea también

[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
