---
title: "Cómo: serializar estructuras mediante PInvoke | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2ebda5f17b94fa28a5eb5222ccc991119ec4f81a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Cómo: serializar estructuras mediante PInvoke
Este documento explica cómo a funciones nativas que aceptan cadenas de estilo C pueden llamarse desde las funciones administradas que proporcionan una instancia de <xref:System.String> mediante el uso de P/Invoke. Aunque recomendamos que use las características de interoperabilidad de C++ en lugar de P/Invoke porque P/Invoke proporciona pocos errores en tiempo de compilación reporting, no tiene seguridad de tipos y puede resultar tediosa de implementar, si la API no administrada se empaqueta como un archivo DLL y el código fuente no es está disponible, P/Invoke es la única opción. En caso contrario, consulte los siguientes documentos:  
  
-   [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Cómo: Serializar estructuras mediante PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 De forma predeterminada, estructuras nativas y administradas se distribuyen de manera diferente en la memoria, correctamente estructuras para pasar a través del límite administrado y no es necesario realizar pasos adicionales para preservar la integridad de datos.  
  
 Este documento explican los pasos necesarios para definir equivalentes administrados de estructuras nativas y cómo se pueden pasar las estructuras resultantes a funciones no administradas. Este documento se da por supuesto que simple estructuras: aquellos que no contienen cadenas o punteros: se usan. Para obtener información acerca de la interoperabilidad de no bits/bytes, consulte [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke no pueden tener tipos de no bits/bytes como un valor devuelto. Tipos que pueden o que tienen la misma representación en código no administrado y no administrado. Para obtener más información, consulte [bits/bytes y tipos no-bits/bytes](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3).  
  
 Cálculo de referencias simple, estructuras de bits/bytes a través del límite administrado y primero requiere que se definan versiones administradas de cada estructura nativa. Estas estructuras pueden tener cualquier nombre válido; No hay ninguna relación entre la versión nativa y administrada de las dos estructuras que no sea su distribución de datos. Por lo tanto, es esencial que la versión administrada contiene campos que tienen el mismo tamaño y en el mismo orden que la versión nativa. (No hay ningún mecanismo para garantizar que las versiones administradas y nativas de la estructura son equivalentes, por lo que las incompatibilidades no serán evidentes hasta el tiempo de ejecución. Es responsabilidad del programador asegurarse de que las dos estructuras tienen el mismo diseño de datos).  
  
 Dado que a veces, los miembros de estructuras administradas se reorganizan para optimizar el rendimiento, es necesario utilizar el <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo para indicar que la estructura se disponen secuencialmente. También es una buena idea establecer explícitamente la estructura de configuración para ser el mismo que el utilizado por la estructura nativa de empaquetado. (Aunque de forma predeterminada, Visual C++ utiliza una empaquetado para el código administrado de la estructura de 8 bytes).  
  
1.  A continuación, use <xref:System.Runtime.InteropServices.DllImportAttribute> para declarar puntos de entrada que corresponden a las funciones no administradas que acepte la estructura, pero use la versión administrada de la estructura en las firmas de función, que es un punto sea irrelevante si usa el mismo nombre en ambas versiones de la estructura.  
  
2.  Ahora código administrado puede pasar la versión administrada de la estructura a las funciones no administradas como si fueran funciones administradas realmente. Estas estructuras se pueden pasar por valor o por referencia, como se muestra en el ejemplo siguiente.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente consta de un módulo administrado y no administrado. El módulo no administrado es un archivo DLL que define una estructura llamada Location y una función llamada GetDistance, que acepta dos instancias de la estructura de ubicación. El segundo módulo es una aplicación de línea de comandos administrada que importa la función GetDistance, pero la define en cuanto a un equivalente administrado de la estructura Location: MLocation. En la práctica probablemente se podría utilizar el mismo nombre en ambas versiones de la estructura; Sin embargo, un nombre diferente se usa aquí para mostrar que el prototipo DllImport se define en términos de la versión administrada.  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado utilizando tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con DllImport en tiempo de compilación.  
  
```  
// TraditionalDll3.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#include <stdio.h>  
#include <math.h>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
   #define TRADITIONALDLL_API __declspec(dllexport)  
#else  
   #define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct Location {  
   int x;  
   int y;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API double GetDistance(Location, Location);  
   TRADITIONALDLL_API void InitLocation(Location*);  
}  
  
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
```  
  
## <a name="example"></a>Ejemplo  
  
```  
// MarshalStruct_pi.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MLocation {  
   int x;  
   int y;  
};  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL3.dll")]  
   static public double GetDistance(MLocation, MLocation);  
   [DllImport("TraditionalDLL3.dll")]  
   static public double InitLocation(MLocation*);  
};  
  
int main() {  
   MLocation loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   MLocation loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   double dist = TraditionalDLL::GetDistance(loc1, loc2);  
   Console::WriteLine("[managed] distance = {0}", dist);  
  
   MLocation loc3;  
   TraditionalDLL::InitLocation(&loc3);  
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);  
}  
```  
  
```Output  
[unmanaged] loc1(0,0) loc2(100,100)  
[managed] distance = 141.42135623731  
[unmanaged] Initializing location...  
[managed] x=50 y=50  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)