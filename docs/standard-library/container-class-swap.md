---
title: Clase de contenedor::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450771"
---
# <a name="container-classswap"></a>Clase de contenedor::swap

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Intercambia las secuencias controladas entre **\*this** y su argumento.

## <a name="syntax"></a>Sintaxis

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Comentarios

Si **\*this.get\_allocator ==** _right_ **.get_allocator**, realiza un intercambio en tiempo constante. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)
