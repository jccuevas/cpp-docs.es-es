---
title: "Error del compilador C3468 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3468"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3468"
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3468
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': solamente puede reenviar un tipo a un ensamblado:  
  
 '`file`' no es un ensamblado  
  
 Solo se pueden reenviar tipos de un ensamblado.  
  
 Para obtener más información, consulta [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md).  
  
## Ejemplo  
 En el ejemplo siguiente se crea un módulo.  
  
```  
// C3468.cpp // compile with: /LN /clr public ref class R {};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3468.  
  
```  
// C3468_b.cpp // compile with: /clr /c #using "C3468.netmodule" [ assembly:TypeForwardedTo(R::typeid) ];   // C3468  
```