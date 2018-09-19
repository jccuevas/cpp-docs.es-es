---
title: 'Cómo: serializar matrices mediante PInvoke | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03e3cf184828c33c63c5252344eb0041640729cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132536"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Cómo: serializar matrices mediante PInvoke
Este tema explica cómo a funciones nativas que aceptan cadenas de estilo C se pueden llamar mediante el tipo de cadena CLR <xref:System.String> utilizando el soporte de invocación de plataforma de .NET Framework. Los programadores de Visual C++ se recomienda utilizar las características de interoperabilidad de C++ en su lugar (cuando sea posible) debido a que P/Invoke proporciona pocos errores en tiempo de compilación reporting, no tiene seguridad de tipos y puede resultar tediosa implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción (en caso contrario, vea [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).  
  
## <a name="example"></a>Ejemplo  
 Dado que las matrices nativas y administradas se distribuyen de manera diferente en la memoria, pasarlas correctamente a través del límite administrado y no requiere conversión o el cálculo de referencias. Este tema muestra cómo se puede pasar una matriz de elementos simple (blitable) a funciones nativas desde código administrado.  
  
 Como ocurre en general, la serialización de datos administrado y el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo se usa para crear un punto de entrada administrado para cada función nativa que se usará. En el caso de las funciones que toman matrices como argumentos, la <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo debe usarse también para especificar al compilador cómo se pueden calcular las referencias los datos. En el ejemplo siguiente, la <xref:System.Runtime.InteropServices.UnmanagedType> enumeración se utiliza para indicar que se pueden calcular las referencias de la matriz administrada como una matriz de estilo C.  
  
 El código siguiente consta de un módulo administrado y no administrado. El módulo no administrado es un archivo DLL que define una función que acepta una matriz de enteros. El segundo módulo es una aplicación de línea de comandos administrada que importa esta función, pero lo define en términos de una matriz administrada y usa el <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar que la matriz debe convertirse en una matriz nativa cuando se le llama.  
  
 El módulo administrado se compila con/CLR.  
  
```cpp  
// TraditionalDll4.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);  
}  
  
void TakesAnArray(int len, int a[]) {  
   printf_s("[unmanaged]\n");  
   for (int i=0; i<len; i++)  
      printf("%d = %d\n", i, a[i]);  
}  
```  
  
```cpp  
// MarshalBlitArray.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL4.dll")]  
   static public void TakesAnArray(  
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);  
};  
  
int main() {  
   array<int>^ b = gcnew array<int>(3);  
   b[0] = 11;  
   b[1] = 33;  
   b[2] = 55;  
   TraditionalDLL::TakesAnArray(3, b);  
  
   Console::WriteLine("[managed]");  
   for (int i=0; i<3; i++)  
      Console::WriteLine("{0} = {1}", i, b[i]);  
}  
```  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional #include (directiva). De hecho, dado que se tiene acceso a la DLL en tiempo de ejecución solo, problemas con las funciones se importan con <xref:System.Runtime.InteropServices.DllImportAttribute> no se detectarán durante la compilación.  
  
## <a name="see-also"></a>Vea también  
 [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)