---
title: barrera | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c220106d62bf65505c9c5b48085a9ee3e67fe0cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415036"
---
# <a name="barrier"></a>barrier

Sincroniza todos los subprocesos en un equipo; todos los subprocesos se detendrá en la barrera, hasta que todos los subprocesos ejecuten la barrera.

## <a name="syntax"></a>Sintaxis

```
#pragma omp barrier
```

## <a name="remarks"></a>Comentarios

El `barrier` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.3 barrier (directiva)](../../../parallel/openmp/2-6-3-barrier-directive.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar `barrier`, consulte [maestro](../../../parallel/openmp/reference/master.md).

## <a name="see-also"></a>Vea también

[Directivas](../../../parallel/openmp/reference/openmp-directives.md)