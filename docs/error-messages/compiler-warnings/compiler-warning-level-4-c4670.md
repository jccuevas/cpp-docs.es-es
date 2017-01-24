---
title: "Advertencia del compilador (nivel 4) C4670 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4670"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4670"
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4670
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': no se puede obtener acceso a esta clase base  
  
 La clase base especificada de un objeto para que se produzca en un bloque **try** no es accesible. No se puede crear una instancia del objeto. Compruebe que la clase base se hereda con el especificador de acceso correcto.  
  
 El ejemplo siguiente genera la advertencia C4670:  
  
```  
// C4670.cpp // compile with: /EHsc /W4 class A { }; class B : /* public */ A { } b;   // inherits A with private access by default int main() { try { throw b;   // C4670 } catch( B ) { } }  
```