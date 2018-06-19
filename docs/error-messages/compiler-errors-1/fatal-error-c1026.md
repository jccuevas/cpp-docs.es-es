---
title: Error irrecuperable C1026 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24c034d45b7f8b222471094f4580902ae1b8dc66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198110"
---
# <a name="fatal-error-c1026"></a>Error irrecuperable C1026
desbordamiento de la pila del analizador, programa demasiado complejo  
  
 El espacio necesario para analizar el sistema produjo un desbordamiento de pila del compilador.  
  
 Reduzca la complejidad de las expresiones:  
  
-   Reduciendo el anidamiento en `for` y `switch` las instrucciones. Colocar instrucciones más profundamente anidadas en funciones independientes.  
  
-   Descomponiendo las expresiones largas que utilicen operadores coma o llamadas de función.