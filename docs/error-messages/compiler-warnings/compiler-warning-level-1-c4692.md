---
title: Advertencia del compilador (nivel 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: e7ec657956c72f1e321227d54b796164292f0c0e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052489"
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