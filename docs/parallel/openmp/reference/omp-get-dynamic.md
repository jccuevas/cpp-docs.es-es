---
title: omp_get_dynamic () | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2b5a285ef019cd1752b60065f7040d9a937ce38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389894"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic

Devuelve un valor que indica si el número de subprocesos disponibles en la región paralela posteriores puede ser ajustado por el tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
int omp_get_dynamic();
```

## <a name="return-value"></a>Valor devuelto

Si es distinto de cero, realizar un ajuste dinámico de subprocesos está habilitado.

## <a name="remarks"></a>Comentarios

Realizar un ajuste dinámico de subprocesos se especifica con [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) y [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).

Para obtener más información, consulte [3.1.7 omp_set_dynamic (función)](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

## <a name="example"></a>Ejemplo

Consulte [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) para obtener un ejemplo del uso de `omp_get_dynamic`.

## <a name="see-also"></a>Vea también

[Funciones](../../../parallel/openmp/reference/openmp-functions.md)