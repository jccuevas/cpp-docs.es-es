---
title: "Error del compilador C2801 | Microsoft Docs"
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
  - "C2801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2801"
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operador' debe ser un miembro no estático  
  
 Los operadores siguientes se pueden sobrecargar sólo como miembros no estáticos:  
  
-   Asignación `=`  
  
-   Acceso a miembros de clase `->`  
  
-   Subíndices `[]`  
  
-   Llamada a función `()`  
  
 Posibles causas del error C2801:  
  
-   El operador sobrecargado no es un miembro de clase, estructura o unión  
  
-   El operador sobrecargado se ha declarado como `static`.  
  
-   El código siguiente genera el error C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```