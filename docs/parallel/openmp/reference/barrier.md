---
title: barrera | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0008c343130bf47170957204793cf3c85b22f1e3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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