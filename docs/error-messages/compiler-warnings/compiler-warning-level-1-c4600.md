---
title: "Advertencia del compilador (nivel 1) C4600 | Microsoft Docs"
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
  - "C4600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4600"
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma 'nombre de macro' : esperaba una cadena válida con contenido  
  
 No se puede especificar una cadena vacía al realizar una operación push o pop en un nombre de macro con las macros [pop\_macro](../../preprocessor/pop-macro.md) o [push\_macro](../../preprocessor/push-macro.md).  
  
 El código siguiente genera el error C4600:  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```