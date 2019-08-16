---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 7b573127518969accdfdcc4a25a50269dd6aa002
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456403"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

La macro _ITERATOR_DEBUG_LEVEL controla si [](../standard-library/checked-iterators.md) se habilitan los iteradores comprobados y la [compatibilidad con iteradores](../standard-library/debug-iterator-support.md) de depuración. Esta macro reemplaza y combina la funcionalidad de las macros _SECURE_SCL y _HAS_ITERATOR_DEBUGGING anteriores.

## <a name="macro-values"></a>Valores de la macro

En la tabla siguiente se resumen los posibles valores de la macro _ITERATOR_DEBUG_LEVEL.

|Modo de compilación|Valor de la macro|DESCRIPCIÓN|
|----------------------|----------------|-----------------|
|**Depuración**|||
||0|Deshabilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||1|Habilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||2 (predeterminado)|Habilita la depuración de iteradores. Los iteradores comprobados no son pertinentes.|
|**Release**|||
||0 (predeterminado)|Deshabilita los iteradores comprobados.|
||1|Habilita los iteradores comprobados. La depuración de iteradores no es pertinente.|

En el modo de lanzamiento, el compilador genera un error si se especifica _ITERATOR_DEBUG_LEVEL como 2.

## <a name="remarks"></a>Comentarios

La macro _ITERATOR_DEBUG_LEVEL controla si [](../standard-library/checked-iterators.md) se habilitan los iteradores comprobados y en modo de depuración si está habilitada la [compatibilidad con iteradores](../standard-library/debug-iterator-support.md) de depuración. Si _ITERATOR_DEBUG_LEVEL se define como 1 o 2, los iteradores comprobados garantizan que los límites de los contenedores no se sobrescriban. Si _ITERATOR_DEBUG_LEVEL es 0, los iteradores no se comprueban. Cuando _ITERATOR_DEBUG_LEVEL se define como 1, el uso de iteradores Unsafe produce un error en tiempo de ejecución y el programa finaliza. Cuando _ITERATOR_DEBUG_LEVEL se define como 2, el uso de iteradores Unsafe produce una aserción y un cuadro de diálogo de error en tiempo de ejecución que le permite interrumpir el depurador.

Dado que la macro _ITERATOR_DEBUG_LEVEL admite una funcionalidad similar a las macros _SECURE_SCL y _HAS_ITERATOR_DEBUGGING, puede que no esté seguro de qué macro y valor de macro usar en una situación determinada. Para evitar confusiones, se recomienda usar solo la macro _ITERATOR_DEBUG_LEVEL. En esta tabla se describe el valor de la macro _ITERATOR_DEBUG_LEVEL equivalente que se usa para los distintos valores de _SECURE_SCL y _HAS_ITERATOR_DEBUGGING en el código existente.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valor predeterminado de versión)|0 (deshabilitado)|0 (deshabilitado)|
|1|1 (habilitado)|0 (deshabilitado)|
|2 (valor predeterminado de depuración)|(no pertinente)|1 (habilitado en modo de depuración)|

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Ejemplo

Para especificar un valor para la macro _ITERATOR_DEBUG_LEVEL, use una opción del compilador [/d](../build/reference/d-preprocessor-definitions.md) para definirlo en la línea de `#define` comandos o C++ use antes de que los encabezados de la biblioteca estándar se incluyan en los archivos de código fuente. Por ejemplo, en la línea de comandos, para compilar *sample. cpp* en modo de depuración y para usar la compatibilidad con el iterador de depuración, puede especificar la definición de la macro _ITERATOR_DEBUG_LEVEL:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

En un archivo de código fuente, especifique la macro antes de los encabezados de la biblioteca estándar que definen los iteradores.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Vea también

[Iteradores comprobados](../standard-library/checked-iterators.md)\
[Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)\
[Bibliotecas seguras: biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)
