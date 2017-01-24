---
title: "C&#243;mo: Calcular las referencias de punteros incrustados mediante PInvoke | Microsoft Docs"
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
  - "cálculo de referencias de datos [C++], punteros incrustados"
  - "punteros incrustados [C++]"
  - "interoperabilidad [C++], punteros incrustados"
  - "calcular las referencias [C++], punteros incrustados"
  - "invocación de plataforma [C++], punteros incrustados"
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de punteros incrustados mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede llamar a las funciones que se implementan en archivos DLL no administrados desde código administrado utilizando la funcionalidad de invocación de plataforma \(P\/Invoke\).  Si el código fuente para el archivo DLL no está disponible, P\/Invoke es la única opción para interoperar.  Sin embargo, al contrario que en otros lenguajes de .NET, Visual C\+\+ proporciona una alternativa a P\/Invoke.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md) y [Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).  
  
## Ejemplo  
 El paso de estructuras a código nativo requiere la creación de una estructura administrada que sea equivalente a la estructura nativa en cuanto a la distribución de los datos.  Sin embargo, las estructuras que contienen punteros requieren un tratamiento especial.  Para cada puntero incrustado en la estructura nativa, la versión administrada de la estructura debe contener una instancia del tipo <xref:System.IntPtr>.  Además, la memoria para estas instancias se debe asignar, inicializar y liberar explícitamente utilizando los métodos <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A> y <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>.  
  
 El código siguiente está compuesto por módulo administrado y en uno no administrado.  El módulo no administrado es un archivo DLL que define una función que acepta una estructura llamada ListString que contiene un puntero y una función llamada TakesListStruct.  El módulo administrado es una aplicación de línea de comandos que importa la función TakesListStruct y define una estructura llamada MListStruct que es equivalente a la ListStruct nativa excepto en que double\* se representa con una instancia <xref:System.IntPtr>.  Antes de llamar a TakesListStruct, la función principal asigna e inicializa la memoria a la que hace referencia este campo.  
  
 El módulo administrado se compila con \/clr, pero \/clr:pure también funciona.  
  
```  
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
  
```  
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
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional directiva \#include.  De hecho, sólo se puede obtener acceso al archivo DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con <xref:System.Runtime.InteropServices.DllImportAttribute> en tiempo de compilación.  
  
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)