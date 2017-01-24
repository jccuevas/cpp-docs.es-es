---
title: "C&#243;mo: Calcular las referencias de matrices mediante la interoperabilidad de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], calcular las referencias"
  - "interoperabilidad de C++, matrices"
  - "cálculo de referencias de datos [C++], matrices"
  - "interoperabilidad [C++], matrices"
  - "calcular las referencias [C++], matrices"
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de matrices mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra un aspecto de la interoperabilidad de Visual C\+\+.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo pasar una matriz administrada a una función no administrada.  La función administrada utiliza [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md) para suprimir la recolección de elementos no utilizados para la matriz antes de llamar a la función no administrada.  Si se proporciona la función no administrada con un puntero anclado en el montón GC, la sobrecarga de crear una copia de la matriz se puede evitar.  Para mostrar que la función no administrada tiene acceso a la memoria del montón GC, modifica el contenido de la matriz y los cambios se reflejan cuando la función administrada reanuda el control.  
  
```  
// PassArray1.cpp  
// compile with: /clr  
#ifndef _CRT_RAND_S  
#define _CRT_RAND_S  
#endif  
  
#include <iostream>  
#include <stdlib.h>  
using namespace std;  
  
using namespace System;  
  
#pragma unmanaged  
  
void TakesAnArray(int* a, int c) {  
   cout << "(unmanaged) array received:\n";  
   for (int i=0; i<c; i++)  
      cout << "a[" << i << "] = " << a[i] << "\n";  
  
   unsigned int number;  
   errno_t err;  
  
   cout << "(unmanaged) modifying array contents...\n";  
   for (int i=0; i<c; i++) {  
      err = rand_s( &number );  
      if ( err == 0 )  
         a[i] = number % 100;  
   }  
}  
  
#pragma managed  
  
int main() {  
   array<int>^ nums = gcnew array<int>(5);  
  
   nums[0] = 0;  
   nums[1] = 1;  
   nums[2] = 2;  
   nums[3] = 3;  
   nums[4] = 4;  
  
   Console::WriteLine("(managed) array created:");  
   for (int i=0; i<5; i++)  
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);  
  
   pin_ptr<int> pp = &nums[0];  
   TakesAnArray(pp, 5);  
  
   Console::WriteLine("(managed) contents:");  
   for (int i=0; i<5; i++)  
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra el paso de una matriz no administrada a una función administrada.  La función administrada tiene acceso a la memoria de la matriz directamente \(al contrario que si se crea una matriz administrada y se copia el contenido de la matriz\), lo que permite reflejar los cambios realizados mediante la función administrada en la función no administrada cuando recupera el control.  
  
```  
// PassArray2.cpp  
// compile with: /clr   
#include <iostream>  
using namespace std;  
  
using namespace System;  
  
#pragma managed  
  
void ManagedTakesAnArray(int* a, int c) {  
   Console::WriteLine("(managed) array received:");  
   for (int i=0; i<c; i++)  
      Console::WriteLine("a[{0}] = {1}", i, a[i]);  
  
   cout << "(managed) modifying array contents...\n";  
   Random^ r = gcnew Random(DateTime::Now.Second);  
   for (int i=0; i<c; i++)  
      a[i] = r->Next(100);  
}  
  
#pragma unmanaged  
  
void NativeFunc() {  
   int nums[5] = { 0, 1, 2, 3, 4 };  
  
   printf_s("(unmanaged) array created:\n");  
   for (int i=0; i<5; i++)  
      printf_s("a[%d] = %d\n", i, nums[i]);  
  
   ManagedTakesAnArray(nums, 5);  
  
   printf_s("(ummanaged) contents:\n");  
   for (int i=0; i<5; i++)  
      printf_s("a[%d] = %d\n", i, nums[i]);  
}  
  
#pragma managed  
  
int main() {  
   NativeFunc();  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)