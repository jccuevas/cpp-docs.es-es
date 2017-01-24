---
title: "Advertencia del compilador (nivel 1) C4683 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4683"
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***función* ': el origen de eventos tiene un parámetro 'out'; tenga cuidado al enlazar controladores de eventos múltiples**  
  
 Si hay más de un receptor de eventos escuchando un origen de eventos COM, puede que se pase por alto el valor de un parámetro out.  
  
 Tenga en cuenta que se producirá una pérdida de memoria en las situaciones siguientes:  
  
1.  Si un método tiene un parámetro out asignado internamente, por ejemplo BSTR \*.  
  
2.  Si el evento tiene más de un controlador \(evento de multidifusión\).  
  
 El motivo de la pérdida de memoria es que el parámetro out está establecido mediante más de un controlador, pero sólo el último controlador lo devuelve al emplazamiento de la llamada.  
  
 El código siguiente genera el error C4683:  
  
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