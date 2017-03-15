---
title: "C&#243;mo: Calcular las referencias de punteros a funci&#243;n mediante PInvoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cálculo de referencias de datos [C++], devoluciones de llamada y delegados"
  - "interoperabilidad [C++], devoluciones de llamada y delegados"
  - "calcular las referencias [C++], devoluciones de llamada y delegados"
  - "invocación de plataforma [C++], devoluciones de llamada y delegados"
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Calcular las referencias de punteros a funci&#243;n mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo se pueden utilizar delegados administrados en lugar de punteros a función al interoperar con funciones no administradas utilizando características de P\/Invoke en .NET Framework.  Sin embargo, se aconseja a los programadores de Visual C\+\+ que utilicen las características de interoperabilidad de C\+\+ en lugar de lo indicado \(cuando sea posible\), ya que P\/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y su implementación puede resultar tediosa.  Si la API no administrada se empaqueta como archivo DLL y el código fuente no está disponible, P\/Invoke es la única opción.  De lo contrario, vea los temas siguientes:  
  
-   [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Cómo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 Se puede llamar desde código administrado a las API no administradas que toman punteros a funciones como argumentos, con un delegado administrado en lugar del puntero a función nativa.  El compilador calcula automáticamente las referencias del delegado a funciones no administradas como un puntero a función e inserta el código necesario de transición entre administrado y no administrado.  
  
## Ejemplo  
 El código siguiente está compuesto por módulo administrado y en uno no administrado.  El módulo no administrado es un archivo DLL que define una función llamada TakesCallback que acepta un puntero a función.  Esta dirección se utiliza para ejecutar la función.  
  
 El módulo administrado define un delegado cuyas referencias se calculan para el código nativo como un puntero a función y utiliza el atributo <xref:System.Runtime.InteropServices.DllImportAttribute> para exponer la función TakesCallback nativa ante el código administrado.  En la función principal, se crea una instancia del delegado y se pasa a la función TakesCallback.  El resultado del programa muestra que esta función es ejecutada por la función nativa TakesCallback.  
  
 La función administrada suprime la recolección de elementos no utilizados para el delegado administrado, para evitar que la recolección de elementos no utilizados en .NET Framework cambie la ubicación del delegado durante la ejecución de la función nativa.  
  
 El módulo administrado se compila con \/clr, pero \/clr:pure también funciona.  
  
```  
// TraditionalDll5.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   /* Declare an unmanaged function type that takes two int arguments  
      Note the use of __stdcall for compatibility with managed code */  
   typedef int (__stdcall *CALLBACK)(int);  
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);  
}  
  
int TakesCallback(CALLBACK fp, int n) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n);  
}  
```  
  
```  
// MarshalDelegate.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
public delegate int GetTheAnswerDelegate(int);  
public value struct TraditionalDLL {  
   [DllImport("TraditionalDLL5.dll")]  
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);  
};  
  
int GetNumber(int n) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
   return x + n;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TraditionalDLL::TakesCallback(fp, 42);  
}  
```  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional directiva \#include.  De hecho, sólo se puede obtener acceso al archivo DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con <xref:System.Runtime.InteropServices.DllImportAttribute> en tiempo de compilación.  
  
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)