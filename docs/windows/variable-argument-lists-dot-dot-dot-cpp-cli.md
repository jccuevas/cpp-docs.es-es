---
title: Listas de argumentos variables (...) (C++ / C++ / CLI) | Microsoft Docs
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
ms.openlocfilehash: 054d91881d136564cdfb956f240789ca5a425ef2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642947"
---
# <a name="variable-argument-lists--ccli"></a>Listas de argumentos de variables (...) (C++/CLI)
En este ejemplo se muestra cómo puede usar el `...` sintaxis de Visual C++ para implementar las funciones que tienen un número variable de argumentos.  
  
> [!NOTE]
>  En este tema pertenece a C++ / c++ / CLI. Para obtener información sobre el uso de la `...` en ISO Standard C++, vea [puntos suspensivos y plantillas Variádicas](../cpp/ellipses-and-variadic-templates.md) y elipses y argumentos predeterminados en [expresiones de postfijo](../cpp/postfix-expressions.md).  
  
 El parámetro que utiliza `...` debe ser el último parámetro en la lista de parámetros.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
```cpp  
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
 El ejemplo siguiente muestra cómo llamar desde C#, una función de Visual C++ que toma un número variable de argumentos.  
  
```cpp  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 La función `f` se puede llamar desde C# o Visual Basic, por ejemplo, como si fuese una función que puede tomar un número variable de argumentos.  
  
 En C#, un argumento que se pasa a un `ParamArray` parámetro puede llamarse mediante un número variable de argumentos. Es el siguiente ejemplo de código en C#.  
  
```cs  
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
  
 Una llamada a `f` en Visual C++ puede pasar una matriz inicializado o una matriz de longitud variable.  
  
```cpp  
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