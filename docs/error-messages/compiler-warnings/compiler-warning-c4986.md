---
title: "Advertencia del compilador C4986 | Microsoft Docs"
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
  - "C4986"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4986"
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4986
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“función”: la especificación de excepciones no coincide con la declaración anterior  
  
 Esta advertencia puede representarse cuando hay una especificación de excepciones en una declaración y no en la otra.  
  
 De forma predeterminada, la advertencia C4986 está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4986.  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1()  
{  
    // ...  
}  
  
```  
  
## Ejemplo  
 El ejemplo siguiente elimina esta advertencia.  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1() throw (X*)  
{  
    // ...  
}  
  
```