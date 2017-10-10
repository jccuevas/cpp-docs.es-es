---
title: Error irrecuperable C1026 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 187cfc1a59fc40a721be09aef9e78ef36c68f66a
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1026"></a>Error irrecuperable C1026
desbordamiento de la pila del analizador, programa demasiado complejo  
  
 El espacio necesario para analizar el sistema produjo un desbordamiento de pila del compilador.  
  
 Reduzca la complejidad de las expresiones:  
  
-   Reduciendo el anidamiento en `for` y `switch` las instrucciones. Colocar instrucciones más profundamente anidadas en funciones independientes.  
  
-   Descomponiendo las expresiones largas que utilicen operadores coma o llamadas de función.
