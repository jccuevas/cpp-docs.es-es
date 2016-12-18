---
title: "C&#243;mo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C++ | Microsoft Docs"
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
  - "interoperabilidad de C++, punteros incrustados"
  - "cálculo de referencias de datos [C++], punteros incrustados"
  - "interoperabilidad [C++], punteros incrustados"
  - "calcular las referencias [C++], punteros incrustados"
  - "punteros [C++], calcular las referencias"
  - "estructuras [C++], calcular las referencias de punteros incrustados"
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo se puede llamar a una función no administrada que toma una estructura que contiene punteros desde una función administrada.  La función administrada crea una instancia de la estructura e inicializa el puntero incrustado con la nueva palabra clave \(en lugar de la palabra clave [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)\).  Dado que así se asigna la memoria en el montón nativo, no hay ninguna necesidad de anclar la matriz para suprimir la recolección de elementos no utilizados.  Sin embargo, la memoria se debe eliminar explícitamente para evitar pérdidas en ella.  
  
```  
// marshal_embedded_pointer.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// unmanaged struct  
struct ListStruct {  
   int count;  
   double* item;  
};  
  
#pragma unmanaged  
  
void UnmanagedTakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
  
#pragma managed  
  
int main() {  
   ListStruct list;  
   list.count = 10;  
   list.item = new double[list.count];  
  
   Console::WriteLine("[managed] count = {0}", list.count);  
   Random^ r = gcnew Random(0);  
   for (int i=0; i<list.count; i++) {  
      list.item[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);  
   }  
  
   UnmanagedTakesListStruct( list );  
   delete list.item;  
}  
```  
  
  **recuento \[administrado\] \= 10**  
**array\[0\] \= 72,624326996796**  
**array\[1\] \= 81,7325359590969**  
**array\[2\] \= 76,8022689394663**  
**array\[3\] \= 55,8161191436537**  
**array\[4\] \= 20,6033154021033**  
**array\[5\] \= 55,8884794618415**  
**array\[6\] \= 90,6027066011926**  
**array\[7\] \= 44,2177873310716**  
**array\[8\] \= 97,754975314138**  
**array\[9\] \= 27,370445768987**  
**recuento \[no administrado\] \= 10**  
**array\[0\] \= 72,624327**  
**array\[1\] \= 81,732536**  
**array\[2\] \= 76,802269**  
**array\[3\] \= 55,816119**  
**array\[4\] \= 20,603315**  
**array\[5\] \= 55,888479**  
**array\[6\] \= 90,602707**  
**array\[7\] \= 44,217787**  
**array\[8\] \= 97,754975**  
**array\[9\] \= 27,370446**   
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)