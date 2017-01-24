---
title: "Advertencia del compilador (nivel 1) C4489 | Microsoft Docs"
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
  - "C4489"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4489"
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4489
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'especificador' : no se permite en el método de interfaz 'método'; los especificadores de reemplazo solamente se admiten en métodos de clase ref y de clase value  
  
 Se ha utilizado incorrectamente una palabra clave de especificador en un método de interfaz.  
  
 Para obtener más información, vea [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4489.  
  
```  
// C4489.cpp  
// compile with: /clr /c /W1  
public interface class I {   
   void f() new;   // C4489  
   virtual void b() override;   // C4489  
  
   void g();   // OK  
};  
```