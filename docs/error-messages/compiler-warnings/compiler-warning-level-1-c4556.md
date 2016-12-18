---
title: "Advertencia del compilador (nivel 1) C4556 | Microsoft Docs"
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
  - "xml"
  - "C4556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4556"
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el valor del argumento inmediato intrínseco 'valor' está fuera del intervalo 'límiteinferior \- límitesuperior'  
  
 Un argumento intrínseco coincide con una instrucción máquina.  La instrucción máquina tiene un número fijo de bits para codificar la constante.  Si ***value*** se encuentra fuera del intervalo, no se codificará correctamente.  El compilador trunca los bits adicionales.  
  
 El código siguiente genera el error C4556:  
  
```  
// C4556.cpp  
// compile with: /W1  
// processor: x86 IPF  
#include <xmmintrin.h>  
void test()  
{  
   __m64 m;  
   _m_pextrw(m, 5);   // C4556  
}  
int main()  
{  
}  
```