---
title: Clase de contenedor::erase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="container-classerase"></a>Clase de contenedor::erase

> [!NOTE]
> Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

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
