---
title: 'Cómo: serializar punteros incrustados mediante PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 68545e7b25d0faacbc829ac6ae8ae1022b8963b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438436"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Cómo: serializar punteros incrustados mediante PInvoke

Funciones que se implementan en archivos DLL no administrado se pueden llamar desde código administrado mediante la funcionalidad de invocación de plataforma (P/Invoke). Si el código fuente para el archivo DLL no está disponible, P/Invoke es la única opción para interoperar. Sin embargo, a diferencia de otros lenguajes. NET, Visual C++ proporciona una alternativa a P/Invoke. Para obtener más información, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md) y [Cómo: serializar incrustado punteros Using C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

## <a name="example"></a>Ejemplo

Pasar estructuras a código nativo requiere que se crea una estructura administrada equivalente en términos de diseño de datos a la estructura nativa. Sin embargo, las estructuras que contienen punteros requieren un tratamiento especial. Para cada puntero incrustado en la estructura nativa, la versión administrada de la estructura debe contener una instancia de la <xref:System.IntPtr> tipo. Además, memoria para estas instancias se deben asignar explícitamente, inicializado y libere mediante la <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, y <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> métodos.

El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una función que acepta una estructura denominada ListString que contiene un puntero y una función llamada TakesListStruct. El módulo administrado es una aplicación de línea de comandos que importa la función TakesListStruct y define una estructura denominada MListStruct que es equivalente a la ListStruct nativa salvo que el doble * se representa con un <xref:System.IntPtr> instancia. Antes de llamar a TakesListStruct, la función principal asigna e inicializa la memoria que hace referencia este campo.

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que los problemas con las funciones que se importan con <xref:System.Runtime.InteropServices.DllImportAttribute> no se detectarán en tiempo de compilación.

## <a name="see-also"></a>Vea también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)