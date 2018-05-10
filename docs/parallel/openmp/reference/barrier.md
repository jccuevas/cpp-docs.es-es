---
title: barrera | Documentos de Microsoft
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
ms.openlocfilehash: bf5b2cd9edf54e58c06e7d2a48529393cd3ced64
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="barrier"></a>barrier
Sincroniza todos los subprocesos en un equipo; todos los subprocesos se sitúe en la barrera, hasta que todos los subprocesos ejecutan la barrera.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>Comentarios  
 El `barrier` directiva es compatible con ningún cláusulas de OpenMP.  
  
 Para obtener más información, consulte [2.6.3 barrier (directiva)](../../../parallel/openmp/2-6-3-barrier-directive.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `barrier`, consulte [principal](../../../parallel/openmp/reference/master.md).  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)