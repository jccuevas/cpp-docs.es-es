---
title: "Compiler Error C3386 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3386"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3386"
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Compiler Error C3386
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : \_\_declspec\(dllexport\)\/\_\_declspec\(dllimport\) no se pueden aplicar a un tipo WinRT o administrado  
  
 Los modificadores `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` no son válidos en un tipo de Windows en tiempo de ejecución o administrado.  
  
 El ejemplo siguiente genera el error C3386 y muestra cómo corregirlo:  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```