---
title: "Advertencia del compilador (nivel 4) C4434 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4434"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4434"
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 4) C4434
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un constructor de clase debe tener accesibilidad privada; se cambiará a acceso privado  
  
 La advertencia C4434 indica que el compilador ha cambiado la accesibilidad de un constructor estático.  Los constructores estáticos deben tener accesibilidad privada, ya que están concebidos para que sólo los llame Common Language Runtime.  Para obtener más información, vea [Constructores estáticos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```