---
title: Error del compilador C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165618"
---
# <a name="compiler-error-c3813"></a>Error del compilador C3813

una declaración de propiedad solo puede aparecer en la definición de un tipo WinRT o administrado

Una [propiedad](../../dotnet/how-to-use-properties-in-cpp-cli.md) solo se puede declarar dentro de un tipo de Windows Runtime o administrado. Los tipos nativos no admiten la palabra clave `property`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3813 y se muestra cómo corregirlo:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```
