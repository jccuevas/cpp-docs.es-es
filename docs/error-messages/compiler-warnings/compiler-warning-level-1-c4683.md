---
title: Compilador advertencia (nivel 1) C4683 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0a8ca498a3c95a1b37229f6ac973cf74a8e28ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4683"></a>Advertencia del compilador (nivel 1) C4683
**'**   
 ***función* ': origen de eventos tiene un 'out': parámetro; tenga cuidado al enlazar varios controladores de eventos**  
  
 Si más de un receptor de eventos está realizando escuchas para un origen de eventos COM, se puede omitir el valor de un parámetro de salida.  
  
 Tenga en cuenta que se producirá una pérdida de memoria en la situación siguiente:  
  
1.  Si un método tiene un parámetro out asignado internamente, por ejemplo una cadena BSTR *.  
  
2.  Si el evento tiene más de un controlador (es un evento de multidifusión)  
  
 El motivo de la pérdida de es que el parámetro de salida se definido por más de un controlador, pero para el sitio de llamada sólo devuelve el último controlador.  
  
 El ejemplo siguiente genera C4683:  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```