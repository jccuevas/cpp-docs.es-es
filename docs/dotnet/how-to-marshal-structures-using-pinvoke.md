---
title: 'Cómo: serializar estructuras mediante PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: fe5d2cf4804baea286827e9d5e270c10cd587b30
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545202"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Cómo: serializar estructuras mediante PInvoke

En este documento se explica cómo se puede llamar a las funciones nativas que aceptan estructuras de estilo C desde funciones administradas mediante P/Invoke. Aunque se recomienda usar las características de C++ interoperabilidad en lugar de p/Invoke porque p/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y puede ser tedioso de implementar, si la API no administrada se empaqueta como un archivo dll y el código fuente no está disponible, P/Invoke es la única opción. En caso contrario, consulte los siguientes documentos:

- [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Cómo: Serializar cadenas mediante PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

De forma predeterminada, las estructuras nativas y administradas se colocan de forma diferente en la memoria, por lo que pasar correctamente las estructuras a través del límite administrado/no administrado requiere pasos adicionales para conservar la integridad de los datos.

En este documento se explican los pasos necesarios para definir equivalentes administrados de estructuras nativas y cómo se pueden pasar las estructuras resultantes a funciones no administradas. En este documento se da por supuesto que se usan estructuras simples (las que no contienen cadenas o punteros). Para obtener información sobre la interoperabilidad sin bits por bytes, vea [usar C++ Interop (implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke no puede tener tipos que no pueden transferirse en bytes como un valor devuelto. Los tipos que pueden transferirse en bytes tienen la misma representación en código administrado y no administrado. Para obtener más información, vea [tipos que no](/dotnet/framework/interop/blittable-and-non-blittable-types)pueden transferirse en bytes y sin bits.

Para calcular las referencias de las estructuras simples y sin bits a través del límite administrado o no administrado, primero es necesario definir las versiones administradas de cada estructura nativa. Estas estructuras pueden tener cualquier nombre válido; no hay ninguna relación entre la versión nativa y la versión administrada de las dos estructuras que no sean su diseño de datos. Por lo tanto, es fundamental que la versión administrada contenga campos que tengan el mismo tamaño y en el mismo orden que la versión nativa. (No hay ningún mecanismo para asegurarse de que las versiones administradas y nativas de la estructura son equivalentes, por lo que las incompatibilidades no se volverán evidentes hasta el tiempo de ejecución. Es responsabilidad del programador asegurarse de que las dos estructuras tienen el mismo diseño de datos).

Dado que los miembros de las estructuras administradas a veces se reorganizan por motivos de rendimiento, es necesario usar el atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> para indicar que la estructura se ha diseñado secuencialmente. También es una buena idea establecer explícitamente el valor de empaquetado de la estructura para que sea el mismo que el utilizado por la estructura nativa. (Aunque de forma predeterminada, C++ visual usa un empaquetado de estructura de 8 bytes para el código administrado).

1. A continuación, use <xref:System.Runtime.InteropServices.DllImportAttribute> para declarar puntos de entrada que correspondan a las funciones no administradas que aceptan la estructura, pero que usan la versión administrada de la estructura en las signaturas de función, que es un punto de Moot si utiliza el mismo nombre para ambas versiones de la estructura.

1. Ahora, el código administrado puede pasar la versión administrada de la estructura a las funciones no administradas como si fueran realmente funciones administradas. Estas estructuras se pueden pasar por valor o por referencia, tal y como se muestra en el ejemplo siguiente.

## <a name="example"></a>Ejemplo

El siguiente código consta de un módulo administrado y no administrado. El módulo no administrado es un archivo DLL que define una estructura denominada Location y una función denominada GetDistance que acepta dos instancias de la estructura Location. El segundo módulo es una aplicación de línea de comandos administrada que importa la función GetDistance, pero la define en términos de un equivalente administrado de la estructura de ubicación, MLocation. En la práctica, el mismo nombre probablemente se utilizaría para ambas versiones de la estructura. sin embargo, aquí se usa un nombre diferente para demostrar que el prototipo DllImport se define en términos de la versión administrada.

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la Directiva de #include tradicional. De hecho, solo se tiene acceso al archivo DLL en tiempo de ejecución, por lo que no se detectarán problemas con las funciones importadas con DllImport en tiempo de compilación.

```cpp
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

```cpp
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

## <a name="see-also"></a>Consulte también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
