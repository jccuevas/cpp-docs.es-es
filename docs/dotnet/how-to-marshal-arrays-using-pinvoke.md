---
title: "C&#243;mo: Calcular las referencias a matrices mediante PInvoke | Microsoft Docs"
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
  - "cálculo de referencias de datos [C++], matrices"
  - "interoperabilidad [C++], matrices"
  - "calcular las referencias [C++], matrices"
  - "invocación de plataforma [C++], matrices"
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias a matrices mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema, se explica cómo se puede llamar a funciones nativas que aceptan cadenas de lenguaje C mediante el tipo de cadena de CLR <xref:System.String> utilizando la compatibilidad de invocación de plataforma \(P\/Invoke\) de .NET Framework.  Se aconseja a los programadores de Visual C\+\+ que utilicen las características de interoperabilidad de C\+\+ en lugar de lo indicado \(cuando sea posible\), ya que P\/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y su implementación puede resultar tediosa.  Si la API no administrada se empaqueta como archivo DLL y el código fuente no está disponible, P\/Invoke es la única opción \(en caso contrario, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)\).  
  
## Ejemplo  
 Dado que las matrices nativas y administradas se distribuyen de manera diferente en memoria, para pasarlas correctamente por el límite entre administrado y no administrado se requiere conversión o cálculo de referencias.  En este tema, se muestra cómo se puede pasar una matriz de elementos simples \(representables como bits o bytes\) a funciones nativas desde código administrado.  
  
 Como sucede con el cálculo de referencias de datos administrados\/no administrados en general, el atributo <xref:System.Runtime.InteropServices.DllImportAttribute> se utiliza para crear un punto de entrada administrado para cada función nativa que se va a usar.  En el caso de funciones que toman matrices como argumentos, también se debe utilizar el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para especificar al compilador cómo se efectuará el cálculo de referencias de los datos.  En el ejemplo siguiente, la enumeración <xref:System.Runtime.InteropServices.UnmanagedType> se utiliza para indicar que el cálculo de referencias de la matriz administrada se efectuará como para una matriz de estilo C.  
  
 El código siguiente está compuesto por módulo administrado y en uno no administrado.  El módulo no administrado es un archivo DLL que define una función que acepta una matriz de enteros.  El segundo módulo es una aplicación de línea de comandos administrada que importa esta función, pero la define en cuanto a una matriz administrada, y utiliza el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para especificar que la matriz se debe convertir en una matriz nativa cuando se le llame.  
  
 El módulo administrado se compila con \/clr, pero \/clr:pure también funciona.  
  
```  
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
  
```  
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
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional directiva \#include.  De hecho, dado que sólo se puede obtener acceso al archivo DLL en tiempo de ejecución, no se detectarán problemas con funciones importadas con <xref:System.Runtime.InteropServices.DllImportAttribute> en tiempo de compilación.  
  
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)