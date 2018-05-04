---
title: STACKSIZE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2093762b3c6f21d319c53a85da5ec5b430a1fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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