---
title: "Error matemático M6111 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 204df0df4855fd2628a96ac326dd39c0d65151e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6111"></a>Error matemático M6111
subdesbordamiento de la pila  
  
 Una operación de punto flotante generó un subdesbordamiento de la pila en el coprocesador 8087/287/387 o en el emulador.  
  
 Este error suele causarlo una llamada a un `long double` función que no devuelve un valor. Por ejemplo, el siguiente genera este error cuando se compila y se ejecuta:  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 El programa termina con el código de salida 139.