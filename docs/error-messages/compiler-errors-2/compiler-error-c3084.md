---
title: Error del compilador C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 01e229fe0ae5bf9e04c577bb653ff1ed7fdb33bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243289"
---
# <a name="compiler-error-c3084"></a>Error del compilador C3084

'function': un finalizador o destructor no puede ser 'keyword'

Se declaró un destructor o finalizador de forma incorrecta.

Por ejemplo, un destructor no debería marcarse como sealed.  El destructor no será accesible para los tipos derivados.  Para obtener más información, consulte [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md) y [destructores y finalizadores en cómo: Definir y utilizar clases y structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3084.

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```