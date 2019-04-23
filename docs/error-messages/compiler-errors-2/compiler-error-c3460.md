---
title: Error del compilador C3460
ms.date: 11/04/2016
f1_keywords:
- C3460
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
ms.openlocfilehash: 9ffbc5102855574aba668a2c501cd08dbaebe5b8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777944"
---
# <a name="compiler-error-c3460"></a>Error del compilador C3460

'type': solamente se puede reenviar un tipo definido por el usuario

Para obtener más información, consulte [reenvío de tipos (C++ / c++ / CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un componente.

```
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3460.

```
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```