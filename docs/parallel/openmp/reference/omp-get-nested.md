---
title: omp_get_nested () | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59900f0a1aba1cbc3bacc5cd1d8832e60aebe30b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686885"
---
# <a name="ompgetnested"></a>omp_get_nested
Devuelve un valor que indica si está habilitado el paralelismo anidado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int omp_get_nested( );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si está habilitado el paralelismo es distinto de cero, anidado.  
  
## <a name="remarks"></a>Comentarios  
 Paralelismo anidado se especifica con [omp_set_nested ()](../../../parallel/openmp/reference/omp-set-nested.md) y [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).  
  
 Para obtener más información, consulte [3.1.10 omp_get_nested (función)](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [omp_set_nested ()](../../../parallel/openmp/reference/omp-set-nested.md) para obtener un ejemplo del uso de `omp_get_nested`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../../parallel/openmp/reference/openmp-functions.md)