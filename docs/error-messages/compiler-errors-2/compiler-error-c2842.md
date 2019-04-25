---
title: Error del compilador C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382949"
---
# <a name="compiler-error-c2842"></a>Error del compilador C2842

> '*clase*': tipo administrado o tipo de WinRT no puede definir su propio 'operator new' u 'operator delete'

## <a name="remarks"></a>Comentarios

Puede definir sus propios **new (operador)** o **operador delete** para administrar la asignación de memoria en el montón nativo. Sin embargo, las clases de referencia no pueden definir estos operadores porque solo se asignan en el montón administrado.

Para obtener más información, consulte [operadores definidos por el usuario (C++ / c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Ejemplo

El código siguiente genera el error C2842.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
