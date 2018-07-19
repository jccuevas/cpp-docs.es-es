---
title: Clase de contenedor::reference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13883e1426be22c8cf3d329be33258c69511900d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966024"
---
# <a name="container-classreference"></a>Clase de contenedor::reference

> [!NOTE]
> Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Describe un objeto que puede actuar como una referencia a un elemento de la secuencia controlada.

## <a name="syntax"></a>Sintaxis

```

typedef T2 reference;
```

## <a name="remarks"></a>Comentarios

Se describe como sinónimo del tipo sin especificar `T2` (normalmente `Alloc::reference`). Un objeto de tipo `reference` puede convertirse en un objeto de tipo [const_reference](../standard-library/container-class-const-reference.md).

## <a name="see-also"></a>Vea también

[Clase contenedora de ejemplo](../standard-library/sample-container-class.md)<br/>
