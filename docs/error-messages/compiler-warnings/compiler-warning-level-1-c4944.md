---
title: Advertencia del compilador (nivel 1) C4944
ms.date: 11/04/2016
f1_keywords:
- C4944
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
ms.openlocfilehash: 339a136824f050391c23e268992a656714d1dabb
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050231"
---
# <a name="compiler-warning-level-1-c4944"></a>Advertencia del compilador (nivel 1) C4944

'symbol': no se puede importar un símbolo desde 'assembly1': ya que 'symbol' ya existe en el ámbito actual.

Se definió un símbolo en un archivo de código fuente y, a continuación, una instrucción #using hizo referencia a un ensamblado que también define el símbolo. Se ha ignorado el símbolo en el ensamblado.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un componente con un tipo llamado ClassA.

```csharp
// C4944.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

## <a name="example"></a>Ejemplo

Los ejemplos siguientes generan C4944.

```cpp
// C4944b.cpp
// compile with: /clr /W1
class ClassA {
public:
   int u;
};

#using "C4944.dll"   // C4944 ClassA also defined C4944.dll

int main() {
   ClassA * x = new ClassA();
   x->u = 9;
   System::Console::WriteLine(x->u);
}
```