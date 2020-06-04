---
title: 'Bibliotecas seguras: Biblioteca estándar de C++'
ms.date: 11/04/2016
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: e352489ca12b5815aab5517defc72571abe177fb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446095"
---
# <a name="safe-libraries-c-standard-library"></a>Bibliotecas seguras: Biblioteca estándar de C++

Se han realizado varias mejoras en las bibliotecas que se suministran con C++Microsoft, incluida C++ la biblioteca estándar, para que sean más seguras.

Varios métodos de la biblioteca estándar de C++ se identificaron como potencialmente inseguros porque podrían provocar una saturación del búfer u otro defecto de código. El uso de estos métodos no es recomendable. Se crearon nuevos métodos más seguros para reemplazarlos. Todos estos nuevos métodos terminan en `_s`.

También se realizaron varias mejoras para que los iteradores y los algoritmos sean más seguros. Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md), [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md) y [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Observaciones

En la tabla siguiente se detallan los métodos de la biblioteca estándar de C++ que son potencialmente inseguros, así como sus equivalentes más seguros:

|Método potencialmente inseguro|Equivalente más seguro|
|-------------------------------|----------------------|
|[copy](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[copy](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Si se llama a cualquiera de los métodos potencialmente inseguros detallados más arriba, o si usan incorrectamente los iteradores, el compilador generará la [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Para obtener información sobre cómo deshabilitar estas advertencias, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>En esta sección

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Iteradores comprobados](../standard-library/checked-iterators.md)

[Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Consulte también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)
