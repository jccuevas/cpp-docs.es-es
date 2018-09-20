---
title: compartido (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 118fa1eb75e8b943b6b490c158e5e21522d57e6c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441335"
---
# <a name="shared-openmp"></a>shared (OpenMP)

Especifica que una o más variables deben compartirse entre todos los subprocesos.

## <a name="syntax"></a>Sintaxis

```
shared(var)
```

### <a name="parameters"></a>Parámetros

*var*<br/>
Una o más variables para compartir. Si se especifica más de una variable, separe los nombres de variable con una coma.

## <a name="remarks"></a>Comentarios

Otra manera de compartir variables entre subprocesos es con el [copyprivate](../../../parallel/openmp/reference/copyprivate.md) cláusula.

`shared` se aplica a las siguientes directivas:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [Secciones](../../../parallel/openmp/reference/sections-openmp.md)

Para obtener más información, consulte [2.7.2.4 compartido](../../../parallel/openmp/2-7-2-4-shared.md).

## <a name="example"></a>Ejemplo

Consulte [privada](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo del uso de `shared`.

## <a name="see-also"></a>Vea también

[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)