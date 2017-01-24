---
title: "Error del compilador C2719 | Microsoft Docs"
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
  - "C2719"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2719"
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2719
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter': el parámetro formal con \_\_declspec\(align\('\#'\)\) no se alineará  
  
 El modificador [align](../../cpp/align-cpp.md) `__declspec` no está permitido en parámetros de función.  La alineación de los parámetros de función se controla mediante la convención de llamada que se utiliza.  Para más información, vea [Convenciones de llamada](../../cpp/calling-conventions.md).  
  
 El siguiente ejemplo genera el error C2719 y muestra cómo corregirlo:  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```