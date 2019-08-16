---
title: Error del compilador C3645
ms.date: 11/04/2016
f1_keywords:
- C3645
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
ms.openlocfilehash: f733de6920e00f1f53c87884a7a334e575bceb06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385789"
---
# <a name="compiler-error-c3645"></a>Error del compilador C3645

'function': no se puede utilizar __clrcall en funciones compiladas para código nativo

La presencia de algunas palabras clave en una función hará que la función se compile en código nativo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3645.

```
// C3645.cpp
// compile with: /clr /c
#pragma unmanaged
int __clrcall dog() {}   // C3645
```