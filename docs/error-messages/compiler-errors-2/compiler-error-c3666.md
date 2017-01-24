---
title: "Error del compilador C3666 | Microsoft Docs"
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
  - "C3666"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3666"
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3666
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructor' : el especificador de reemplazo 'palabra clave' no se permite en un constructor  
  
 Se ha utilizado un especificador de reemplazo en un constructor y es algo que no está permitido.  Para obtener más información, vea [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3666.  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```