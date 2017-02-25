---
title: "Error del compilador C2842 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2842"
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Error del compilador C2842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': un tipo de WinRT o administrado no puede definir su propio 'operator new' u 'operator delete'  
  
 Puede definir sus propios [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md) o [operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md) para administrar la asignación de memoria en el montón nativo.  Sin embargo, las clases de referencia no pueden definir estos operadores porque solo se asignan en el montón administrado.  
  
 Para obtener más información, vea [Operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## Ejemplo  
 El código siguiente genera el error C2842.  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
  
## Ejemplo  
 El código siguiente genera el error C2842.  
  
```  
// C2842_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```