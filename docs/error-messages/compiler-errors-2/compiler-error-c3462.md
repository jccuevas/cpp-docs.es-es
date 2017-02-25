---
title: "Error del compilador C3462 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3462"
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': solamente se puede reenviar un tipo importado.  
  
 El atributo TypeForwardedTo debe aplicarse a un tipo de los metadatos a los que se hace referencia.  
  
 Para obtener más información, consulta [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md).  
  
## Ejemplo  
 En el ejemplo siguiente se crea un componente.  
  
```  
// C3462.cpp // compile with: /clr /LD public ref class R {};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3462.  
  
```  
// C3462b.cpp // compile with: /clr /c #using "C3462.dll" ref class N {}; [assembly:TypeForwardedTo(N::typeid)];   // C3462 [assembly:TypeForwardedTo(R::typeid)];  
```