---
title: omp_set_num_threads () | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae9dbe52dba47208844b73175f20edcc591a3ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444949"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads

Establece el número de subprocesos en posteriores regiones en paralelo, a menos que se reemplaza por un [num_threads](../../../parallel/openmp/reference/num-threads.md) cláusula.

## <a name="syntax"></a>Sintaxis

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parámetros

*num_threads*<br/>
El número de subprocesos en la región paralela.

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [3.1.1 omp_set_num_threads (función)](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

## <a name="example"></a>Ejemplo

Consulte [omp_get_num_threads ()](../../../parallel/openmp/reference/omp-get-num-threads.md) para obtener un ejemplo del uso de `omp_set_num_threads`.

## <a name="see-also"></a>Vea también

[Funciones](../../../parallel/openmp/reference/openmp-functions.md)