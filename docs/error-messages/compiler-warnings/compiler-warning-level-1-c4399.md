---
title: Compilador advertencia (nivel 1) C4399 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aedad6aed07a6056f74ad338037a7268c722627f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703725"
---
# <a name="compiler-warning-level-1-c4399"></a>Advertencia del compilador (nivel 1) C4399

> '*símbolo*': símbolo de por proceso no se debe marcar con __declspec (dllimport) cuando se compila con/CLR: pure

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

No se pueden importar datos de una imagen nativa o una imagen con construcciones nativas y CLR en una imagen pura. Para resolver esta advertencia, compile con **/CLR** (no **/CLR: pure**) o eliminar `__declspec(dllimport)`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```