---
title: Advertencia del compilador (nivel 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: f5db6bf366c86a716be33539feb0085ac03a9647
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683157"
---
# <a name="compiler-warning-level-4-c4564"></a>Advertencia del compilador (nivel 4) C4564

el método ' Method ' de la clase ' Class ' define el parámetro predeterminado no compatible ' Parameter '

El compilador detectó un método con uno o más parámetros con valores predeterminados. Los valores predeterminados de los parámetros se omitirán cuando se invoque el método; especifique explícitamente los valores para esos parámetros. Si no especifica explícitamente los valores para esos parámetros, el C++ compilador generará un error.

Dado el siguiente archivo. dll creado con Visual Basic, que permite parámetros predeterminados en argumentos de método:

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

Y el ejemplo C++ siguiente que usa el archivo. dll creado con Visual Basic,

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```