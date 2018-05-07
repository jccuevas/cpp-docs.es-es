---
title: Error matemático M6111 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b03937ed442b169b960d573b44c0eb6ebca9660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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