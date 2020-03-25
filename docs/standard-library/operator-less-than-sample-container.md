---
title: operator&lt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: 6ef43fb762c4da71062fc846048f21c0112bfafc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215272"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Sobrecarga el **operador <** para comparar dos objetos de [contenedor](../standard-library/sample-container-class.md)de plantilla de clase.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valor devuelto

Devuelve `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Consulte también

[\<contenedor de ejemplo>](../standard-library/sample-container.md)\
[inicio](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)
