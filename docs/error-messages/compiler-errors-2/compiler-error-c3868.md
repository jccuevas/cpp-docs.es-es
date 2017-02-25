---
title: "Error del compilador C3868 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3868"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3868"
ms.assetid: f0e45c2a-2149-4885-a03b-0d230069f03a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3868
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': las restricciones del parámetro genérico 'parámetro' difieren de las de la declaración  
  
 Las declaraciones deben tener las mismas restricciones genéricas.  Para obtener más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3868.  
  
```  
// C3868.cpp  
// compile with: /clr /c  
interface struct I1;  
  
generic <typename T> ref struct MyStruct;  
generic <typename U> where U : I1 ref struct MyStruct;   // C3868  
  
// OK  
generic <typename T> ref struct MyStruct2;  
generic <typename U> ref struct MyStruct2;  
  
generic <typename T> where T : I1 ref struct MyStruct3;  
generic <typename U> where U : I1 ref struct MyStruct3;  
```