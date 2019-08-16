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
ms.openlocfilehash: 168785abb09ca198435c301040d7628a6dd12b26
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460153"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Sobrecarga `operator==` para comparar dos objetos de la clase de plantilla [Container](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Valor devuelto

Devuelve `left.` [el](../standard-library/container-class-size.md) [final](../standard-library/container-class-end.md)del [Inicio](../standard-library/container-class-begin.md).`, left.``, right.begin)` ` == right.size && equal(left.`

## <a name="see-also"></a>Vea también

[\<sample container>](../standard-library/sample-container.md)
