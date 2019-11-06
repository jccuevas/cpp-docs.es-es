---
title: Advertencia del compilador (nivel 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: 6e0f7ab75309994ab306f5caed54724f32e388b1
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624795"
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