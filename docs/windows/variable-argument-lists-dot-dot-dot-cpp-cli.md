---
title: Listas de argumentos variables (...) (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eec0e3591da2417137fda3bae4ed9e7860472fb2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="variable-argument-lists--ccli"></a>Listas de argumentos de variables (...) (C++/CLI)
Este ejemplo muestra cómo se puede utilizar el `...` sintaxis de Visual C++ para implementar funciones que tienen un número variable de argumentos.  
  
> [!NOTE]
>  Este tema corresponde a C++ / CLI. Para obtener información sobre el uso de la `...` en ISO C++ estándar, consulte [puntos suspensivos y plantillas Variádicas](../cpp/ellipses-and-variadic-templates.md) y elipse y argumentos predeterminados en [expresiones de postfijo](../cpp/postfix-expressions.md).  
  
 El parámetro que usa `...` debe ser el último parámetro en la lista de parámetros.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
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
  
### <a name="output"></a>Salida  
  
```  
3  
```  
  
## <a name="code-example"></a>Ejemplo de código  
 En el ejemplo siguiente se muestra cómo llamar a desde C#, una función de Visual C++ que toma un número variable de argumentos.  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 La función `f` pueden llamarse desde C# o Visual Basic, por ejemplo, como si fuese una función que puede tomar un número variable de argumentos.  
  
 En C#, un argumento que se pasa a un `ParamArray` parámetro puede llamarse mediante un número variable de argumentos. El ejemplo de código siguiente es en C#.  
  
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
  
 Una llamada a `f` en Visual C++, puede pasar una matriz inicializada o una matriz de longitud variable.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Matrices](../windows/arrays-cpp-component-extensions.md)