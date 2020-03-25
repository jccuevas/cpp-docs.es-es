---
title: Advertencia del compilador (nivel 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: 0e8e951d5ea50cc755d26616cf23e48c27b2ca84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175368"
---
# <a name="compiler-warning-level-1-c4692"></a>Advertencia del compilador (nivel 1) C4692

'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo_nativo'

Un tipo visible fuera del ensamblado incluye una función miembro cuya firma contiene un tipo nativo no visible fuera del ensamblado. Por consiguiente, no se debería llamar a la función miembro si se crean instancias de su tipo fuera del ensamblado.

Para obtener más información, vea [visibilidad de tipos](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4692.

```cpp
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```
