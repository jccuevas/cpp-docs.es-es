---
title: Clase de contenedor::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1463a854c314884f0b3b6bffa5d37dfb7fec4a6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454509"
---
# <a name="container-classerase"></a>Clase de contenedor::erase

> [!NOTE]
> Este tema se encuentra en la C++ documentación de Microsoft como un ejemplo no funcional de contenedores usados en C++ la biblioteca estándar. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

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

La primera función miembro quita el elemento de la secuencia controlada a la que apunta *_Where*. La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Ambas devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [end](../standard-library/container-class-end.md) si no existe ese elemento.

Las funciones miembro producen una excepción solo si una operación de copia produce una excepción.

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)
