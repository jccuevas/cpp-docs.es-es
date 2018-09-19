---
title: Error del compilador C3828 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a4a414a881aced6e537c0b98e69896aeeb4c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085490"
---
# <a name="compiler-error-c3828"></a>Error del compilador C3828

'tipo de objeto': no se permiten al crear instancias de administrado de argumentos de colocación o WinRTclasses

Al crear un objeto de un tipo administrado o en tiempo de ejecución de Windows, no se puede usar el formato de la ubicación del operador [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) o [nuevo](../../cpp/new-operator-cpp.md).

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