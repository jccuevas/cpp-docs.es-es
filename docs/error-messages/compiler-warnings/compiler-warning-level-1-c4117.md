---
title: Advertencia del compilador (nivel 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 97fd5703a744448db87634e313678cf4e824df7f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626286"
---
# <a name="compiler-warning-level-1-c4117"></a>Advertencia del compilador (nivel 1) C4117

el nombre de macro 'name' está reservado; se omite 'Command'

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Se intenta definir o anular la definición de una macro predefinida.

1. Se intenta definir o anular la definición del operador de preprocesador **defined**.

El ejemplo siguiente genera la advertencia C4117:

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```