---
title: Error del compilador C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: fd52b434f86bdc93124c6005bbf7fadad3cb56b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757064"
---
# <a name="compiler-error-c2492"></a>Error del compilador C2492

'*variable*': es posible que los datos con duración de almacenamiento de subprocesos no tengan interfaz dll

La variable se declara con el atributo [Thread](../../cpp/thread.md) y con la interfaz dll. No se conoce la dirección de la variable `thread` hasta el tiempo de ejecución, por lo que no se puede vincular a una importación o exportación de un archivo DLL.

En el ejemplo siguiente se genera C2492:

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
