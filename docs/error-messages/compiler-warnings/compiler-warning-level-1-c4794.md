---
title: Del compilador (nivel 1) de la advertencia C4794 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4794
dev_langs:
- C++
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6e6b8aedacc71291afc2a34a6a11d7b19a126b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027406"
---
# <a name="compiler-warning-level-1-c4794"></a>Advertencia del compilador (nivel 1) C4794

Segmento de la variable de almacenamiento local 'variable' que cambió de 'section name' a '.tls$'

Usó [#pragma data_seg](../../preprocessor/data-seg.md) para colocar una variable tls en una sección que no comenzaba por .tls$.

La sección .tls$*x* existirá en el archivo objeto donde están definidas las variables [__declspec(thread)](../../cpp/thread.md) . Una sección .tls del archivo EXE o DLL será el resultado de estas secciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4794:

```
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```