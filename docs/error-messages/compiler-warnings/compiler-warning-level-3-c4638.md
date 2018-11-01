---
title: Advertencia del compilador (nivel 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 1bdd7541e16f5c02756678ae78a777094b5fe588
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651534"
---
# <a name="compiler-warning-level-3-c4638"></a>Advertencia del compilador (nivel 3) C4638

> Destino del comentario del documento XML: referencia a símbolo desconocido '*símbolo*'

## <a name="remarks"></a>Comentarios

El compilador no pudo resolver un símbolo (*símbolo*). El símbolo debe ser válido en la compilación.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4638:

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```