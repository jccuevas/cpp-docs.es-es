---
title: operator== (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 08adfcc770551d3050daa46c870b950e468c95b3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150647"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Sobrecarga `operator==` para comparar dos objetos de [contenedor](../standard-library/sample-container-class.md)de plantilla de clase.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valor devuelto

Devuelve `left.`[tamaño](../standard-library/container-class-size.md) `== right.size && equal(left.`[inicio](../standard-library/container-class-begin.md)`, left.`[final](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Consulte también

[\<sample container>](../standard-library/sample-container.md)
