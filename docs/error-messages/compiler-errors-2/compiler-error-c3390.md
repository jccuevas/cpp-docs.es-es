---
title: Error del compilador C3390 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3390
dev_langs:
- C++
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc731f714976d8ab32c5e7a629d008fde008a218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252965"
---
# <a name="compiler-error-c3390"></a>Error del compilador C3390
'type_arg': argumento de tipo no válido para el parámetro genérico 'param' de 'generic_type' genérico; debe ser un tipo de referencia  
  
Se crearon instancias de un tipo genérico incorrectamente.  Compruebe la definición de tipo.  Para más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
El primer ejemplo utiliza C# para crear un componente que contiene un tipo genérico que tiene ciertas restricciones que no se admiten al crear tipos genéricos en C++ / CLR. Para obtener más información, vea [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3390.cs  
// Compile by using: csc /target:library C3390.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Cuando el componente C3390.dll está disponible, el ejemplo siguiente genera la advertencia C3390.  
  
```cpp  
// C3390_b.cpp  
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>  
ref class R { R(int) {} };  
value class V {};  
ref struct N { N() {} };  
  
int main () {  
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type  
   GR<R^, V, N^>^ gr2b; // OK  
}  
```