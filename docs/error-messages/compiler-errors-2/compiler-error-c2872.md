---
title: "Error del compilador C2872 | Microsoft Docs"
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
  - "C2872"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2872"
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2872
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : símbolo ambiguo  
  
 El compilador no puede determinar a qué símbolo se está haciendo referencia.  
  
 El error C2872 se produce si un archivo de encabezado incluye una [using \(directiva\)](../../misc/using-directive-cpp.md), y el archivo de encabezado siguiente está especificado con `#include` y contiene un tipo que también está en el espacio de nombres especificado en la directiva `using`.  Especifique una directiva `using` sólo después de que todos los archivos de encabezado se hayan especificado con `#include`.  
  
 Para obtener información adicional sobre C2872, vea [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;316317](http://support.microsoft.com/default.aspx?scid=kb;en-us;316317).  
  
 El código siguiente genera el error C2872:  
  
```  
// C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok  
   A::i++;   // ok  
   i++;   // C2872 ::i or A::i?  
}  
```