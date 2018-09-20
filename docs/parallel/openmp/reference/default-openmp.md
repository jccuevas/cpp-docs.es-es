---
title: predeterminado (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- default
dev_langs:
- C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea32f473d96c8f48c6628d8f71212269bd6d345
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392622"
---
# <a name="default-openmp"></a>default (OpenMP)

Especifica el comportamiento de las variables sin ámbito de una región paralela.

## <a name="syntax"></a>Sintaxis

```
default(shared | none)
```

## <a name="remarks"></a>Comentarios

`shared`, que está en vigor si el `default` no se especifica la cláusula, significa que cualquier variable en una región paralela se tratará como si se especificó con el [compartido](../../../parallel/openmp/reference/shared-openmp.md) cláusula. `none` significa que las variables utilizadas en una región paralela que no tienen ámbito con la [privada](../../../parallel/openmp/reference/private-openmp.md), [compartido](../../../parallel/openmp/reference/shared-openmp.md), [reducción](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), o [lastprivate](../../../parallel/openmp/reference/lastprivate.md) cláusula provocará un error del compilador.

`default` se aplica a las siguientes directivas:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Secciones](../../../parallel/openmp/reference/sections-openmp.md)

Para obtener más información, consulte [2.7.2.5 predeterminada](../../../parallel/openmp/2-7-2-5-default.md).

## <a name="example"></a>Ejemplo

Consulte [privada](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo del uso de `default`.

## <a name="see-also"></a>Vea también

[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)