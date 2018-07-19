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
ms.openlocfilehash: 4163542d0ba741e6f0a123cbdcdc44dbbec470d1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957796"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

Los controles de macro _ITERATOR_DEBUG_LEVEL si [iteradores comprobados](../standard-library/checked-iterators.md) y [compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md) están habilitadas. Esta macro reemplaza y combina la funcionalidad de las macros anteriores _SECURE_SCL y _HAS_ITERATOR_DEBUGGING.

## <a name="macro-values"></a>Valores de la macro

En la tabla siguiente se resume los posibles valores para la macro _ITERATOR_DEBUG_LEVEL.

|Modo de compilación|Valor de la macro|Descripción|
|----------------------|----------------|-----------------|
|**Depuración**|||
||0|Deshabilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||1|Habilita los iteradores comprobados y deshabilita la depuración de iteradores.|
||2 (predeterminado)|Habilita la depuración de iteradores. Los iteradores comprobados no son pertinentes.|
|**Release**|||
||0 (predeterminado)|Deshabilita los iteradores comprobados.|
||1|Habilita los iteradores comprobados. La depuración de iteradores no es pertinente.|

En modo de lanzamiento, el compilador genera un error si se especifica _ITERATOR_DEBUG_LEVEL como 2.

## <a name="remarks"></a>Comentarios

Los controles de macro _ITERATOR_DEBUG_LEVEL si [iteradores comprobados](../standard-library/checked-iterators.md) están habilitados y, en modo de depuración, ya sea [compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md) está habilitado. Si _ITERATOR_DEBUG_LEVEL se define como 1 o 2, los iteradores comprobados garantizan que no se sobrescriben los límites de los contenedores. Si _ITERATOR_DEBUG_LEVEL es 0, no se comprueban los iteradores. Cuando _ITERATOR_DEBUG_LEVEL se define como 1, cualquier uso no seguro de iteradores produce un error en tiempo de ejecución y el programa finaliza. Cuando _ITERATOR_DEBUG_LEVEL se define como 2, no seguro de iteradores usar hace que una aserción y aparece un cuadro de diálogo de error en tiempo de ejecución que le permite interrumpirán el depurador.

Dado que la macro _ITERATOR_DEBUG_LEVEL admite una funcionalidad similar a las macros _SECURE_SCL y _HAS_ITERATOR_DEBUGGING, es posible que no sabe con seguridad qué macro y una macro de valor para usar en una situación determinada. Para evitar confusiones, se recomienda que use solo la macro _ITERATOR_DEBUG_LEVEL. Esta tabla describe el valor de macro _ITERATOR_DEBUG_LEVEL equivalente a usar para distintos valores de _SECURE_SCL y _HAS_ITERATOR_DEBUGGING en el código existente.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valor predeterminado de versión)|0 (deshabilitado)|0 (deshabilitado)|
|1|1 (habilitado)|0 (deshabilitado)|
|2 (valor predeterminado de depuración)|(no pertinente)|1 (habilitado en modo de depuración)|

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Ejemplo

Para especificar un valor para la macro _ITERATOR_DEBUG_LEVEL, use un [/D](../build/reference/d-preprocessor-definitions.md) para definirlo en la línea de comandos, o use la opción del compilador `#define` antes de la biblioteca estándar de C++ se incluyen los encabezados en los archivos de origen. Por ejemplo, en la línea de comandos para compilar *sample.cpp* en modo de depuración y usar el soporte técnico de iteradores de depuración, puede especificar la definición de macro _ITERATOR_DEBUG_LEVEL:

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
