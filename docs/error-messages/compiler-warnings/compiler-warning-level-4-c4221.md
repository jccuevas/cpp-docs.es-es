---
title: "Advertencia del compilador (nivel 4) C4221 | Microsoft Docs"
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
  - "C4221"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4221"
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4221
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : 'identificador' : no se puede inicializar utilizando la dirección de la variable automática  
  
 Con las extensiones de Microsoft predeterminadas \(\/Ze\), se puede inicializar un tipo agregado \(**array**, `struct`, o **union**\) con la dirección de una variable local \(automática\).  
  
## Ejemplo  
  
```  
// C4221.c  
// compile with: /W4  
struct S  
{  
   int *i;  
};  
  
void func()  
{  
   int j;  
   struct S s1 = { &j };   // C4221  
}  
  
int main()  
{  
}  
```  
  
 Dichas inicializaciones no se permiten cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).