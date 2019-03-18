---
title: Filtrar Serializar estructuras de uso de PInvoke
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: d5c64a3e93cd85d7e38bac7c0ea3fa3c3301abc9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748000"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Filtrar Serializar estructuras de uso de PInvoke

Este documento explica cómo funciones nativas que acepten las estructuras de estilo C se pueden llamar desde las funciones administradas por mediante P/Invoke. Aunque recomendamos que use las características de interoperabilidad de C++ en lugar de P/Invoke porque P/Invoke proporciona pocos informes, de errores de tiempo de compilación no es seguro para el tipo y puede resultar tedioso de implementar, si la API no administrada se empaqueta como un archivo DLL y el código fuente no es está disponible, P/Invoke es la única opción. En caso contrario, consulte los siguientes documentos:

- [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Cómo: Serializar cadenas mediante PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

De forma predeterminada, las estructuras nativas y administradas se distribuyen de manera diferente en la memoria, correctamente pasar estructuras a través del límite administrado y no requiere pasos adicionales para mantener la integridad de datos.

Este documento explica los pasos necesarios para definir equivalentes administrados de estructuras nativas y cómo se pueden pasar las estructuras resultantes a funciones no administradas. Este documento se da por supuesto que simple estructuras: aquellos que no contienen cadenas o punteros: se usan. Para obtener información acerca de la interoperabilidad de espacio, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke no pueden tener tipos como un valor devuelto. Tipos tienen la misma representación en código administrado y no administrado. Para obtener más información, consulte [Non-bits/bytes tipos](/dotnet/framework/interop/blittable-and-non-blittable-types).

Cálculo de referencias simples, las estructuras de bits/bytes a través del límite y no administrado en primer lugar requiere que versiones administradas de cada estructura nativa se defina. Estas estructuras pueden tener cualquier nombre válido; No hay ninguna relación entre la versión nativa y administrada de las dos estructuras que no sea su distribución de datos. Por lo tanto, es fundamental que la versión administrada contiene campos que son del mismo tamaño y en el mismo orden que la versión nativa. (No hay ningún mecanismo para garantizar que las versiones administradas y nativas de la estructura son equivalentes, por lo que las incompatibilidades no serán evidentes hasta el tiempo de ejecución. Es responsabilidad del programador garantizar que las dos estructuras tienen el mismo diseño de datos).

Dado que los miembros de estructuras administradas a veces se reorganizan para mejorar el rendimiento, es necesario utilizar el <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo para indicar que la estructura se disponen secuencialmente. También es una buena idea establecer explícitamente la estructura de configuración sea la misma que usa la estructura nativa de empaquetado. (Aunque de forma predeterminada, Visual C++ utiliza una empaquetado tanto código administrado de la estructura de 8 bytes).

1. A continuación, use <xref:System.Runtime.InteropServices.DllImportAttribute> para declarar los puntos de entrada que corresponden a las funciones no administradas que acepte la estructura, pero usa la versión administrada de la estructura en las firmas de función, que es un punto sea irrelevante si usa el mismo nombre para ambas versiones de la estructura.

1. Ahora código administrado puede pasar la versión administrada de la estructura a las funciones no administradas como si fueran las funciones administradas realmente. Estas estructuras se pueden pasar por valor o por referencia, como se muestra en el ejemplo siguiente.

## <a name="example"></a>Ejemplo

El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una estructura denominada ubicación y una función llamada GetDistance, que acepta dos instancias de la estructura de ubicación. El segundo módulo es una aplicación de línea de comandos administrada que importa la función GetDistance, pero lo define en términos de un equivalente administrado de la estructura de la ubicación, MLocation. En la práctica probablemente se usaría el mismo nombre para ambas versiones de la estructura. Sin embargo, un nombre diferente se usa aquí para demostrar que el prototipo DllImport se define en términos de la versión administrada.

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con DllImport en tiempo de compilación.

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
