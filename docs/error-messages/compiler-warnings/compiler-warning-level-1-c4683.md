---
title: Compilador advertencia (nivel 1) C4683 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418bf25d565c616d5bc4aaf58361c4f28df298ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285348"
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