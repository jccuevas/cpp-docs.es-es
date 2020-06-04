---
title: Error del compilador C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 7ef22711884dabb83efa8c7ebfdb7648316c12ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205418"
---
# <a name="compiler-error-c2435"></a>Error del compilador C2435

> '*var*': la inicialización dinámica requiere CRT administrado, no se puede compilar con/CLR: Safe

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

La inicialización de la variable de dominio por aplicación global requiere el CRT compilado con `/clr:pure`, que no genera una imagen comprobable.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
