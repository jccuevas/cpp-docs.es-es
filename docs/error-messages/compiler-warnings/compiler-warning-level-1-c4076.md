---
title: Advertencia del compilador (nivel 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200276"
---
# <a name="compiler-warning-level-1-c4076"></a>Advertencia del compilador (nivel 1) C4076

> '*modificador de tipo*': no se puede usar con el tipo '*TypeName*'

## <a name="remarks"></a>Observaciones

Un modificador de tipo, **ya sea con o sin** **signo**, no se puede usar con un tipo no entero. se omite el *modificador de tipo* .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4076; para corregirlo, quite el modificador de tipo **sin signo** :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
