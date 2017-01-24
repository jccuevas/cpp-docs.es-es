---
title: "Advertencia del compilador (nivel 4) C4205 | Microsoft Docs"
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
  - "C4205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4205"
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: declaración de función static en ámbito de función  
  
 Con las extensiones de Microsoft habilitadas \(\/Ze\), las funciones estáticas \(**static**\) pueden declararse dentro de otra función.  La función recibe un ámbito global.  
  
## Ejemplo  
  
```  
// C4205.c  
// compile with: /W4  
void func1()  
{  
   static int func2();  // C4205  
};  
  
int main()  
{  
}  
```  
  
 Dichas inicializaciones no se permiten cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).