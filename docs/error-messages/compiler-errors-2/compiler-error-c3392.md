---
title: Error del compilador C3392 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3392
dev_langs: C++
helpviewer_keywords: C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 12ed6dbcc7351926d51df4aa9e3397f3bb598f10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3392"></a>Error del compilador C3392
'arg_tipo': argumento de tipo no válido para el parámetro genérico 'parámetro' del 'tipo_genérico' genérico, debe tener un constructor sin parámetros público.  
  
 Se crearon incorrectamente instancias de un tipo genérico. Compruebe la definición de tipo. Para obtener más información, consulte [genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente utiliza C# para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos en C++ / CLI. Para obtener más información, vea [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3392.cs  
// Compile by using: csc /target:library C3392.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Cuando el componente C3392.dll está disponible, el ejemplo siguiente genera la advertencia C3392.  
  
```cpp  
// C3392_b.cpp  
// Compile by using: cl /clr C3392_b.cpp  
#using <C3392.dll>  
  
ref class R { R(int) {} };  
ref class N { N() {} };  
  
value class V {};  
  
ref class N2 { public: N2() {} };  
ref class R2 { public: R2() {} };  
  
int main () {  
   GR<R^, V, N^>^ gr1;   // C3392  
   GR<R^, V, N2^>^ gr1a; // OK  
  
   GR<R^, N^, N^>^ gr3;  // C3392  
   GR<R^, V, N2^>^ gr3a; // OK  
  
   GR<R^, V, R^>^ gr4;   // C3392  
   GR<R^, V, R2^>^ gr4a; // OK  
}  
```