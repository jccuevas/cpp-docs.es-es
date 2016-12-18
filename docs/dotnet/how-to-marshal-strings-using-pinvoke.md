---
title: "C&#243;mo: Calcular las referencias de cadenas mediante PInvoke | Microsoft Docs"
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
  - "cálculo de referencias de datos [C++], cadenas"
  - "interoperabilidad [C++], cadenas"
  - "calcular las referencias [C++], cadenas"
  - "invocación de plataforma [C++], cadenas"
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de cadenas mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema, se explica cómo se puede llamar a funciones nativas que aceptan cadenas de lenguaje C mediante el tipo de cadena de CLR System::String utilizando la compatibilidad de invocación de plataforma \(P\/Invoke\) de .NET Framework.  Se aconseja a los programadores de Visual C\+\+ que utilicen las características de interoperabilidad de C\+\+ en lugar de lo indicado \(cuando sea posible\), ya que P\/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y su implementación puede resultar tediosa.  Si la API no administrada se empaqueta como archivo DLL y el código fuente no está disponible, P\/Invoke es la única opción \(en caso contrario, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)\).  
  
 Las cadenas administradas y las no administradas se distribuyen de manera diferente en la memoria, por lo que, para pasar cadenas de funciones administradas a no administradas, es necesario que el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> indique al compilador que inserte los mecanismos de conversión requeridos para el cálculo de referencias de los datos de cadenas de manera correcta y segura.  
  
 Del mismo modo que con las funciones que sólo utilizan tipos de datos intrínsecos, <xref:System.Runtime.InteropServices.DllImportAttribute> se utiliza para declarar puntos de entrada administrados en las funciones nativas, pero para pasar cadenas, en lugar de definir estos puntos de entrada como si tomasen cadenas de lenguaje C, se puede utilizar un identificador al tipo <xref:System.String>.  De este modo, se solicita al compilador que inserte el código que realice la conversión necesaria.  Para cada argumento de función en una función no administrada que toma una cadena, se debe usar el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para indicar que se deben calcular las referencias del objeto String respecto a la función nativa como cadena de lenguaje C.  
  
## Ejemplo  
 El código siguiente está compuesto por un módulo administrado y en uno no administrado.  El módulo no administrado es un archivo DLL que define una función llamada TakesAString, que acepta una cadena ANSI de lenguaje C en forma de char\*.  El módulo administrado es una aplicación de línea de comandos que importa la función TakesAString, pero la define como que toma una cadena System.String administrada en lugar de char\*.  El atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> se utiliza para indicar cómo se deberían calcular las referencias de la cadena administrada cuando se llama a TakesAString.  
  
 El módulo administrado se compila con \/clr, pero \/clr:pure también funciona.  
  
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
  
 Esta técnica provoca la construcción de una copia de la cadena en el montón no administrado, de modo que los cambios en la cadena realizados mediante la función nativa no se reflejarán en la copia administrada de la cadena.  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional directiva \#include.  De hecho, sólo se puede obtener acceso al archivo DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con `DllImport` en tiempo de compilación.  
  
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)