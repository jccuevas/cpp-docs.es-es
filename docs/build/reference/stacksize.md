---
title: STACKSIZE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STACKSIZE
dev_langs: C++
helpviewer_keywords: STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82b33d217e593a35b66bb3530840a739e93082ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="stacksize"></a>STACKSIZE
Establece el tamaño de la pila en bytes.  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>Comentarios  
 Un modo equivalente a establecer la pila es con la [asignaciones de la pila](../../build/reference/stack-stack-allocations.md) (/ de la pila) opción. Consulte la documentación de esa opción para obtener más información sobre la *reservar* y `commit` argumentos.  
  
 Esta opción no tiene ningún efecto en las DLL.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)