---
title: Advertencia del compilador (nivel 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: be402eed4474dd736ab237cfb5c7986741338eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163276"
---
# <a name="compiler-warning-level-1-c4230"></a>Advertencia del compilador (nivel 1) C4230

anachronizmus usado: modificadores/calificadores intercalados; calificador omitido

El uso de un calificador antes de un modificador de Microsoft como `__cdecl` es una práctica no actualizada.

## <a name="example"></a>Ejemplo

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
