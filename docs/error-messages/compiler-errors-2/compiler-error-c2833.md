---
title: "Error del compilador C2833 | Microsoft Docs"
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
  - "C2833"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2833"
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2833
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador operador' no es un operador o tipo reconocido  
  
 La palabra `operator` debe ir seguida de un operador que se desee reemplazar o de un tipo que se desee convertir.  
  
 Para obtener una lista de los operadores que se pueden definir en un tipo administrado, vea [Operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 El código siguiente genera el error C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```