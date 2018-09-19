---
title: predeterminado (OpenMP) | Documentos de Microsoft
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
ms.openlocfilehash: 9fc39951270138e9bd243172b289e7bd96190f14
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692326"
---
# <a name="default-openmp"></a>default (OpenMP)
Especifica el comportamiento de las variables sin ámbito en una región paralela.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
default(shared | none)  
```  
  
## <a name="remarks"></a>Comentarios  
 `shared`, que está en vigor si la `default` no se especifica la cláusula, significa que cualquier variable en una región paralela se tratará como si estuviera especificado con el [compartido](../../../parallel/openmp/reference/shared-openmp.md) cláusula. `none` significa que las variables utilizadas en una región paralela que no tienen como ámbito con la [privada](../../../parallel/openmp/reference/private-openmp.md), [compartido](../../../parallel/openmp/reference/shared-openmp.md), [reducción](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), o [lastprivate](../../../parallel/openmp/reference/lastprivate.md) cláusula provocará un error del compilador.  
  
 `default` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Secciones](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, consulte [2.7.2.5 predeterminado](../../../parallel/openmp/2-7-2-5-default.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [privada](../../../parallel/openmp/reference/private-openmp.md) para obtener un ejemplo del uso de `default`.  
  
## <a name="see-also"></a>Vea también  
 [Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)