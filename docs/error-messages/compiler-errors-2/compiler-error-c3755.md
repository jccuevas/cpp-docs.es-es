---
title: Error del compilador C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 90dc3b7a0e1dbc4e0dc6c42ca722ca1db462fca9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558215"
---
# <a name="compiler-error-c3755"></a>Error del compilador C3755

'delegado': no se puede definir un delegado

Un [delegate (extensiones de componentes de C++)](../../windows/delegate-cpp-component-extensions.md) se pueden declarar pero no definido.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3755.

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Ejemplo

C3755 también puede producirse si intenta crear una plantilla de delegado. El ejemplo siguiente genera C3755.

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```