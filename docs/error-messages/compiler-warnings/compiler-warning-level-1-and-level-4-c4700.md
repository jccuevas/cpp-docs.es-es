---
title: "Advertencia del compilador (niveles 1 y 4) C4700 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4700"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4700"
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (niveles 1 y 4) C4700
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se utilizó la variable local 'nombre' sin inicializar  
  
 Se utilizó la variable local *nombre* sin asignarle primero un valor, lo que puede causar resultados imprevistos.  
  
 El código siguiente genera el error C4700:  
  
```  
// C4700.cpp  
// compile with: /W1  
int main() {  
   int i;  
   return i;   // C4700  
}  
```  
  
 Con [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) ésta es una advertencia de nivel 4.  El código siguiente genera el error C4700:  
  
```  
// C4700b.cpp  
// compile with: /W4 /clr:safe /c  
using namespace System;  
int main() {  
   Int32^ bi;  
   return *bi;   // C4700  
}  
```