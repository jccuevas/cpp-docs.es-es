---
title: copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27afaee16a87ddf428570f7854212eed34634d38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059334"
---
# <a name="copyin"></a>copyin
Permite que los subprocesos tener acceso a valor del subproceso principal, para un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
copyin(var)  
```  
  
## <a name="parameters"></a>Parámetros
  
*var*<br/>
El `threadprivate` variable que se inicializará con el valor de la variable en el subproceso principal, tal como existe antes de la construcción paralela.  
  
## <a name="remarks"></a>Comentarios  
 `copyin` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte [threadprivate](../../../parallel/openmp/reference/threadprivate.md) para obtener un ejemplo del uso de `copyin`.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)