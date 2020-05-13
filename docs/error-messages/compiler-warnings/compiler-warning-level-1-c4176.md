---
title: Advertencia del compilador (nivel 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: e7efe17b9840179bd21a432c2654fadd7e9230c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199997"
---
# <a name="compiler-warning-level-1-c4176"></a>Advertencia del compilador (nivel 1) C4176

'subcomponent': subcomponente desconocido para el explorador de la #pragma component

La pragma **component** incluye un subcomponente no válido. Para excluir las referencias a un nombre concreto, debe utilizar la opción **references** antes del nombre.

## <a name="example"></a>Ejemplo

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
