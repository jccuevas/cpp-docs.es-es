---
title: Clase de contenedor::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: 2c2b87e8cc51248fd3d29df7f361fff92da72957
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494502"
---
# <a name="container-classswap"></a>Clase de contenedor::swap

> [!NOTE]
> Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Intercambia las secuencias controladas entre **\*this** y su argumento.

## <a name="syntax"></a>Sintaxis

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Comentarios

Si **\*this.get\_allocator ==** _right_**.get_allocator**, realiza un intercambio en tiempo constante. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)<br/>
