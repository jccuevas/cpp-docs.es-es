---
title: "Compiler Error C3282 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3282"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3282"
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Compiler Error C3282
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las listas de parámetros genéricos solamente pueden aparecer en clases administradas o WinRT, structs o funciones  
  
 Se ha utilizado incorrectamente una lista de parámetros genéricos.  Para obtener más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 En el siguiente ejemplo se genera el error C3282 y se muestra cómo corregirlo.  
  
```  
// C3282.cpp  
// compile with: /clr /c  
generic <typename T> int x;   // C3282  
  
ref struct GC0 {  
   generic <typename T> int x;   // C3282  
};  
  
// OK  
generic <typename T>  
ref class M {};  
```