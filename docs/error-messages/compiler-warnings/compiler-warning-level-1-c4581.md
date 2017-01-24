---
title: "Advertencia del compilador (nivel 1) C4581 | Microsoft Docs"
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
  - "C4581"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4581"
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4581
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

comportamiento obsoleto: '"cadena1"' se ha reemplazado por 'cadena2' para procesar el atributo  
  
 Este error puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: comprobación de parámetros de los atributos de Visual C\+\+.  
  
 En las versiones anteriores, se aceptaban los valores de atributo, tanto si se incluían entre comillas como si no.  Si el valor es una enumeración, no debe incluirse entre comillas.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4581.  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```