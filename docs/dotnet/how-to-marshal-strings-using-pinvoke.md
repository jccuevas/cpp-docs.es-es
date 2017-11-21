---
title: "Cómo: serializar cadenas mediante PInvoke | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0047c76000d336ce18d2bbbab741dc965c1fbc59
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Cómo: serializar cadenas mediante PInvoke
Este tema explica cómo a funciones nativas que aceptan cadenas de estilo C se pueden llamar mediante la cadena CLR escriba System:: String utilizando el soporte de invocación de plataforma de .NET Framework. Los programadores de Visual C++ se recomienda utilizar las características de interoperabilidad de C++ en su lugar (cuando sea posible) debido a que P/Invoke proporciona pocos errores en tiempo de compilación reporting, no tiene seguridad de tipos y puede resultar tediosa implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción, pero en caso contrario, consulte [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 Las cadenas administradas y están dispuestas de forma diferente en la memoria, por lo que pasar cadenas de funciones no administradas a no administrado requiere el <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para indicar al compilador que inserte los mecanismos de conversión necesaria para el cálculo de referencias de los datos de cadena correctamente y segura.  
  
 Al igual que con las funciones que usan solo los tipos de datos intrínsecos, <xref:System.Runtime.InteropServices.DllImportAttribute> se utiliza para declarar puntos de entrada administrado en las funciones nativas, pero para pasar cadenas, en lugar de definir estos puntos de entrada que toma las cadenas de estilo C, un identificador de la <xref:System.String> tipo puede utilizarse en su lugar. Esto indica al compilador que inserte código que realiza la conversión necesaria. Para cada argumento de función en una función no administrada que toma una cadena, la <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo debe usarse para indicar que se debería serializar el objeto de cadena a la función nativa como una cadena de estilo C.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una función llamada TakesAString, que acepta una cadena de estilo C ANSI en forma de char *. El módulo administrado es una aplicación de línea de comandos que importa la función TakesAString, pero define que toma una System.String administrado en lugar de un valor char\*. El <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo se utiliza para indicar cómo se debería serializar la cadena administrada cuando se llama a TakesAString.  
  
 El módulo administrado se compila con/CLR, pero/CLR: pure también funciona.  
  
```  
// TraditionalDll2.cpp  
// compile with: /LD /EHsc  
#include <windows.h>  
#include <stdio.h>  
#include <iostream>  
  
using namespace std;  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAString(char*);  
}  
  
void TakesAString(char* p) {  
   printf_s("[unmanaged] %s\n", p);  
}  
```  
  
```  
// MarshalString.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL  
{  
   [DllImport("TraditionalDLL2.dll")]  
      static public void   
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);  
};  
  
int main() {  
   String^ s = gcnew String("sample string");  
    Console::WriteLine("[managed] passing managed string to unmanaged function...");  
   TraditionalDLL::TakesAString(s);  
   Console::WriteLine("[managed] {0}", s);  
}  
```  
  
 Esta técnica hace una copia de la cadena debe crearse en el montón no administrado, por lo que los cambios realizados en la cadena mediante la función nativa no se reflejarán en la copia administrada de la cadena.  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que los problemas con las funciones que se importan con `DllImport` no se detectarán durante la compilación.  
  
## <a name="see-also"></a>Vea también  
 [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)