---
title: Clase de contenedor::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 0ef4db1c14942fc896f10095ff2331648d27c820
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221641"
---
# <a name="container-classerase"></a>Clase de contenedor::erase

> [!NOTE]
> Este tema es de Microsoft C++ documentación como un ejemplo funcional de los contenedores usados en el C++ biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Borra un elemento.

## <a name="syntax"></a>Sintaxis

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Comentarios

La primera función miembro quita el elemento de la secuencia controlada señalada por *_Where*. La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Ambas devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [end](../standard-library/container-class-end.md) si no existe ese elemento.

Las funciones miembro producen una excepción solo si una operación de copia produce una excepción.

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)<br/>
