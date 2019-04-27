---
title: Advertencia del compilador (nivel 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: c8d223a286b8d42ca404fbfe7cbc51b67b3dd497
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207493"
---
# <a name="compiler-warning-level-1-c4230"></a>Advertencia del compilador (nivel 1) C4230

ha utilizado un anacronismo: los modificadores y calificadores están intercalados; kvalifikátor que se ignoruje.

Con un calificador delante de un modificador de Microsoft como `__cdecl` es una práctica obsoleta.

## <a name="example"></a>Ejemplo

```
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```