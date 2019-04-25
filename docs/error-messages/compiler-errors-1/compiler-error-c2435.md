---
title: Error del compilador C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166651"
---
# <a name="compiler-error-c2435"></a>Error del compilador C2435

> '*var*': inicialización dinámica requiere CRT administrado; no se puede compilar con/CLR: safe

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Inicialización de la variable global por dominio de aplicación requiere compilada CRT con `/clr:pure`, que no genera una imagen que se pueda comprobar.

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```