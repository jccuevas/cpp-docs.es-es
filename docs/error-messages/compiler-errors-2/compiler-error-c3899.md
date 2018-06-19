---
title: Error del compilador C3899 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f40f1065514437463be06a89f01e067c4324cd2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276001"
---
# <a name="compiler-error-c3899"></a>Error del compilador C3899
'var': no se permite el uso de valor l del miembro de datos initonly directamente dentro de una región paralela en la clase 'class'  
  
 Un [initonly (C++ / CLI)](../../dotnet/initonly-cpp-cli.md) no se puede inicializar el miembro de datos dentro de esa parte de un constructor que se encuentra en un [paralelo](../../parallel/openmp/reference/parallel.md) región.  Esto es porque el compilador realiza una reubicación interna de dicho código, que, efectivamente ya no forma parte del constructor.  
  
 Para resolverlo, inicialice al miembro de datos initonly en el constructor, pero fuera de la región paralela.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3899.  
  
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