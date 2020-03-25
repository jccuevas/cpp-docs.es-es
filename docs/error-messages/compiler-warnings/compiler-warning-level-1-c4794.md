---
title: Advertencia del compilador (nivel 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175121"
---
# <a name="compiler-warning-level-1-c4794"></a>Advertencia del compilador (nivel 1) C4794

Segmento de la variable de almacenamiento local 'variable' que cambió de 'section name' a '.tls$'

Usó [#pragma data_seg](../../preprocessor/data-seg.md) para colocar una variable tls en una sección que no comenzaba por .tls$.

La sección .tls$*x* existirá en el archivo objeto donde están definidas las variables [__declspec(thread)](../../cpp/thread.md) . Una sección .tls del archivo EXE o DLL será el resultado de estas secciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4794:

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```
