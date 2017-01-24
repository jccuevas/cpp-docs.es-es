---
title: "Error del compilador C2698 | Microsoft Docs"
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
  - "C2698"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2698"
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2698
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la declaración using de 'declaración 1' no puede coexistir con la declaración using existente de 'declaración 2'  
  
 Una vez que haya una [declaración using](../../cpp/using-declaration.md) para un miembro de datos, no se permitirá ninguna declaración using en el mismo ámbito que utilice el mismo nombre, ya que sólo se pueden sobrecargar las funciones.  
  
 El código siguiente genera el error C2698:  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```