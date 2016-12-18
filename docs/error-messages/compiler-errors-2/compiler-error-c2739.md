---
title: "Error del compilador C2739 | Microsoft Docs"
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
  - "C2739"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2739"
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2739
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

’number': las dimensiones de la matriz administrada o de WinRT explícita deben estar comprendidas entre 1 y 32  
  
 Una dimensión de matriz no estaba comprendida entre 1 y 32.  
  
 El ejemplo siguiente genera el error C2739 y muestra cómo corregirlo:  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```