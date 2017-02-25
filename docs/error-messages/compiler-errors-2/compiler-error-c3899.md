---
title: "Error del compilador C3899 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3899"
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3899
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : el uso del valor L del miembro de datos initonly no se permite directamente dentro de una región paralela en la clase 'clase'  
  
 Un miembro de datos [initonly](../../dotnet/initonly-cpp-cli.md) no puede inicializarse dentro de la parte de un constructor que se encuentra en una región [parallel](../../parallel/openmp/reference/parallel.md).  Esto se debe a que el compilador realiza una reubicación interna de dicho código, de modo que deja de formar parte del constructor.  
  
 Para resolverlo, inicialice el miembro de datos de initonly en el constructor, pero fuera de la región paralela.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3899.  
  
```  
// C3899.cpp  
// compile with: /clr /openmp  
#include <omp.h>   
  
public ref struct R {  
   initonly int x;  
   R() {  
      x = omp_get_thread_num() + 1000;   // OK  
      #pragma omp parallel num_threads(5)  
      {  
         // cannot assign to 'x' here  
         x = omp_get_thread_num() + 1000;   // C3899  
         System::Console::WriteLine("thread {0}", omp_get_thread_num());  
      }  
      x = omp_get_thread_num() + 1000;   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R;  
   System::Console::WriteLine(r->x);  
}  
```