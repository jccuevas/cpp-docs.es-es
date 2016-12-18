---
title: "Error del compilador C2432 | Microsoft Docs"
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
  - "C2432"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2432"
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2432
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

referencia no válida a datos de 16 bits en 'identificador'  
  
 Se utilizó un registro de 16 bits en un registro de índice o base.  El compilador no admite referencias a datos de 16 bits. Los registros de 16 bits no se pueden usar como registros de índice o base al compilar para código de 32 bits.  
  
 El código siguiente genera el error C2432:  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```