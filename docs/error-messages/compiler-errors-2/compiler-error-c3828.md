---
title: Error del compilador C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: f499bb2a8fd6d3148935daec89835b79d2ff5b49
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777851"
---
# <a name="compiler-error-c3828"></a>Error del compilador C3828

'tipo de objeto': no se permiten al crear instancias de administrado de argumentos de colocación o WinRTclasses

Al crear un objeto de un tipo administrado o en tiempo de ejecución de Windows, no se puede usar el formato de la ubicación del operador [ref new, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) o [nuevo](../../cpp/new-operator-cpp.md).

El ejemplo siguiente genera el error C3828 y muestra cómo corregirlo:

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```