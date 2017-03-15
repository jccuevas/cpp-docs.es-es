---
title: "C&#243;mo: Calcular las referencias de estructuras mediante la interoperabilidad de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "interoperabilidad de C++, estructuras"
  - "cálculo de referencias de datos [C++], estructuras"
  - "interoperabilidad [C++], estructuras"
  - "calcular las referencias [C++], estructuras"
  - "estructuras [C++], calcular las referencias"
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de estructuras mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra un aspecto de la interoperabilidad de Visual C\+\+.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
## Ejemplo  
 En el ejemplo siguiente se pasa una estructura de una función administrada a una función no administrada, por valor y por referencia.  Dado que la estructura de este ejemplo contiene sólo tipos de datos intrínsecos \(vea [Blittable and Non\-Blittable Types](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\), no se requiere ningún cálculo de referencias especial.  Para calcular las referencias de estructuras que no pueden transferirse en bloque de bits, como las que contienen punteros, vea [Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
```  
// PassStruct1.cpp  
// compile with: /clr  
  
#include <stdio.h>  
#include <math.h>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
struct Location {  
   int x;  
   int y;  
};  
  
double GetDistance(Location loc1, Location loc2) {  
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);  
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);  
  
   double h = loc1.x - loc2.x;  
   double v = loc1.y = loc2.y;  
   double dist = sqrt( pow(h,2) + pow(v,2) );  
  
   return dist;  
}  
  
void InitLocation(Location* lp) {  
   printf_s("[unmanaged] Initializing location...\n");  
   lp->x = 50;  
   lp->y = 50;  
}  
  
#pragma managed  
  
int main() {  
   Location loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   Location loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   double dist = GetDistance(loc1, loc2);  
   Console::WriteLine("[managed] distance = {0}", dist);  
  
   Location loc3;  
   InitLocation(&loc3);  
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se pasa una estructura de una función no administrada a una función administrada, por valor y por referencia.  Dado que la estructura de este ejemplo contiene sólo tipos de datos intrínsecos \(vea [Blittable and Non\-Blittable Types](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\), no se requiere ningún cálculo de referencias especial.  Para calcular las referencias de estructuras que no pueden transferirse en bloque de bits, como las que contienen punteros, vea [Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
```  
// PassStruct2.cpp  
// compile with: /clr  
#include <stdio.h>  
#include <math.h>  
using namespace System;  
  
// native structure definition  
struct Location {  
   int x;  
   int y;  
};  
  
#pragma managed  
  
double GetDistance(Location loc1, Location loc2) {  
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);  
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);  
  
   double h = loc1.x - loc2.x;  
   double v = loc1.y = loc2.y;  
   double dist = sqrt( pow(h,2) + pow(v,2) );  
  
   return dist;  
}  
  
void InitLocation(Location* lp) {  
   Console::WriteLine("[managed] Initializing location...");  
   lp->x = 50;  
   lp->y = 50;  
}  
  
#pragma unmanaged  
  
int UnmanagedFunc() {  
   Location loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   Location loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);  
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);  
  
   double dist = GetDistance(loc1, loc2);  
   printf_s("[unmanaged] distance = %f\n", dist);  
  
   Location loc3;  
   InitLocation(&loc3);  
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);  
  
    return 0;  
}  
  
#pragma managed  
  
int main() {  
   UnmanagedFunc();  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)