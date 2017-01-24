---
title: "Listas de argumentos de variables (...) (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices de parámetros"
  - "listas de argumentos variables"
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Listas de argumentos de variables (...) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo utilizar la sintaxis `...` en Visual C\+\+ para implementar funciones que tienen un número variable de argumentos.  
  
> [!NOTE]
>  Este tema pertenece a C\+\+\/CLI.  Para obtener información sobre cómo usar `...` en ISO Standard C\+\+, vea [Puntos suspensivos y plantillas variádicas](../cpp/ellipses-and-variadic-templates.md) y [Elipse y argumentos predeterminados](../misc/ellipses-and-default-arguments.md).  
  
 El parámetro que utiliza `...` debe ser el último parámetro de la lista de parámetros.  
  
## Ejemplo  
  
### Código  
  
```  
// mcppv2_paramarray.cpp  
// compile with: /clr  
using namespace System;  
double average( ... array<Int32>^ arr ) {  
   int i = arr->GetLength(0);  
   double answer = 0.0;  
  
   for (int j = 0 ; j < i ; j++)  
      answer += arr[j];  
  
   return answer / i;  
}  
  
int main() {  
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));  
}  
```  
  
### Resultados  
  
```  
3  
```  
  
## Ejemplo de código  
 El ejemplo siguiente muestra cómo llamar desde C\# a una función de Visual C\+\+ que toma un número variable de argumentos.  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 Puede llamarse a la función `f` desde C\# o Visual Basic, por ejemplo, como si fuera una función que puede tomar un número variable de argumentos.  
  
 En C\#, un argumento que se pasa un parámetro `ParamArray` se puede llamar mediante un número variable de argumentos.  El siguiente ejemplo de código está en C\#:  
  
```  
// mcppv2_paramarray3.cs  
// compile with: /r:mcppv2_paramarray2.dll  
// a C# program  
  
public class X {  
   public static void Main() {  
      // Visual C# will generate a String array to match the   
      // ParamArray attribute  
      C myc = new C();  
      myc.f("hello", "there", "world");  
   }  
}  
```  
  
 Una llamada a `f` en Visual C\+\+ puede pasar una matriz inicializado o una matriz de longitud variable.  
  
```  
// mcpp_paramarray4.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
  
int main() {  
   C ^ myc = gcnew C();  
   myc->f("hello", "world", "!!!");  
}  
```  
  
## Vea también  
 [Matrices](../windows/arrays-cpp-component-extensions.md)