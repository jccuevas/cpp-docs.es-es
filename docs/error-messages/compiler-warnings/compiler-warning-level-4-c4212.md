---
title: Advertencia del compilador (nivel 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: d33e5c60bac657060ffef2a43686a5f737eb11cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161313"
---
# <a name="compiler-warning-level-4-c4212"></a>Advertencia del compilador (nivel 4) C4212

se usó una extensión no estándar: se usaron puntos suspensivos en la declaración de función

El prototipo de función tiene un número variable de argumentos. La definición de función no lo es.

En el ejemplo siguiente se genera C4212:

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```
