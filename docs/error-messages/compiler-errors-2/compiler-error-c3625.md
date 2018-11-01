---
title: Error del compilador C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 08ad1d09cb9149811566f67a585a718340254de9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635410"
---
# <a name="compiler-error-c3625"></a>Error del compilador C3625

'native_type': un tipo nativo no puede derivar de un tipo administrado o WinRT 'type'

Una clase nativa no puede heredarse de una clase administrada o WinRT. Para obtener más información, consulte [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3625:

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
