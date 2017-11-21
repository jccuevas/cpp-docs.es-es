---
title: "Las Variables de ámbito de A.21 con la cláusula privada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 761141b1f71758bb751fbcb29f2c9b395279e174
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21 Variables de ámbito con la cláusula private
Los valores de `i` y `j` en el ejemplo siguiente no está definida en la salida de la región paralela:  
  
```  
int i, j;  
i = 1;  
j = 2;  
#pragma omp parallel private(i) firstprivate(j)  
{  
  i = 3;  
  j = j + 2;  
}  
printf_s("%d %d\n", i, j);  
```  
  
 Para obtener más información sobre la `private` cláusula, vea [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en página 25.