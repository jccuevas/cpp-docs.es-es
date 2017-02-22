---
title: "Advertencia del compilador (nivel 4) C4214 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4214"
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4214
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: tipos de campos de bits distintos de int  
  
 Con las extensiones de Microsoft habilitadas \(\/Ze\), los miembros de estructuras de campos de bits pueden ser de cualquier tipo entero.  
  
## Ejemplo  
  
```  
// C4214.c  
// compile with: /W4  
struct bitfields  
{  
   unsigned short j:4;  // C4214  
};  
  
int main()  
{  
}  
```  
  
 Dichos campos de bits no se permiten cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).