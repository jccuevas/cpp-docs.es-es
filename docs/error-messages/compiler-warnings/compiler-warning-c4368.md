---
title: "Advertencia del compilador C4368 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4368"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4368"
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Advertencia del compilador C4368
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no puede definir 'miembro' como miembro de 'tipo' administrado: no se admiten tipos mixtos  
  
 No puede incrustar un miembro de datos nativo en un tipo CLR.  
  
 Es posible, sin embargo, declarar un puntero a un tipo nativo y controlar su duración en el constructor, destructor y finalizador de la clase administrada.  Para obtener más información, vea [Destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Esta advertencia siempre se emite como error.  Utilice la directiva pragma [warning](../../preprocessor/warning.md) para deshabilitar C4368.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4368.  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```