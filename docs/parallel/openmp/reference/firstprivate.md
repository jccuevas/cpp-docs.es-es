---
title: firstprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d070b8de3cf0382447c3b8e756140892dcd85edc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387125"
---
# <a name="firstprivate"></a>firstprivate

Especifica que cada subproceso debe tener su propia instancia de una variable, y que la variable debe inicializarse con el valor de la variable, porque existe antes de la construcción paralela.

## <a name="syntax"></a>Sintaxis

```
firstprivate(var)
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`var`|La variable a tener instancias en cada subproceso y se inicializará con el valor de la variable, porque existe antes de la construcción paralela. Si se especifica más de una variable, separe los nombres de variable con una coma.|

## <a name="remarks"></a>Comentarios

## <a name="remarks"></a>Comentarios

`firstprivate` se aplica a las siguientes directivas:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [Secciones](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

Para obtener más información, consulte [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo del uso de `firstprivate`, vea el ejemplo de [privada](../../../parallel/openmp/reference/private-openmp.md).

## <a name="see-also"></a>Vea también

[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)