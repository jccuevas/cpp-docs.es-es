---
title: Clase de contenedor::swap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0ac2b3322f7f034c09c86f2307da2e3f3995c0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842331"
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
