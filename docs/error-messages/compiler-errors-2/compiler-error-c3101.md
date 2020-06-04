---
title: Error del compilador C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: dca91b9359417b8c4cce9329e2aa25107016c086
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750005"
---
# <a name="compiler-error-c3101"></a>Error del compilador C3101

expresión no válida para el argumento de atributo con nombre ' Field '

Al inicializar un argumento de atributo con nombre, el valor debe ser una constante de tiempo de compilación.

Para obtener más información sobre los atributos, vea [atributos definidos por el usuario](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3101.

```cpp
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
