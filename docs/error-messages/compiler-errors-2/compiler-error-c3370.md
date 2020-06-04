---
title: Error del compilador C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 7c1a9e4e099fc33dd585e5cdbffa2bbb8ea36987
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755595"
---
# <a name="compiler-error-c3370"></a>Error del compilador C3370

'idl_module name': idl_module no se ha definido aún

Para poder usar [idl_module](../../windows/idl-module.md) para especificar un punto de entrada en un archivo DLL, debe usar `idl_module` primero para especificar el nombre del archivo DLL.

El ejemplo siguiente genera la advertencia C3370:

```cpp
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```
