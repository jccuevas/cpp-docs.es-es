---
title: "Error del compilador C2504 | Microsoft Docs"
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
  - "C2504"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2504"
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2504
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : clase base sin definir  
  
 La clase base se ha declarado pero no está definida.  Causas posibles:  
  
1.  Falta el archivo de inclusión.  
  
2.  No se ha declarado la clase base externa mediante [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
 El código siguiente genera el error C2504:  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 \/\/ OK  
  
```  
class C{};  
class D : public C {};  
```