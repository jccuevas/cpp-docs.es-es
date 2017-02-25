---
title: "Error del compilador C3238 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3238"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3238"
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3238
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': ya se reenvió un tipo con este nombre al ensamblado 'assembly'  
  
 Un tipo se definió en una aplicación cliente que también se definió, a través de la sintaxis de reenvío de tipos, en un ensamblado de referencia. No se pueden definir ambos tipos en el ámbito de la aplicación.  
  
 Vea [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md) para obtener más información.  
  
## Ejemplo  
 En el ejemplo siguiente se crea un ensamblado que contiene un tipo que se reenvió desde otro ensamblado.  
  
```  
// C3238.cpp // compile with: /clr /LD public ref class R {};  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera un ensamblado usado para contener la definición del tipo, pero no solo contiene la sintaxis de reenvío de tipos.  
  
```  
// C3238_b.cpp // compile with: /clr /LD #using "C3238.dll" [ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3238.  
  
```  
// C3238_c.cpp // compile with: /clr /c // C3238 expected // Delete the following line to resolve. #using "C3238_b.dll" public ref class R {};  
```