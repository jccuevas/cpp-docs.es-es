---
title: Advertencia de la línea de comandos D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 62834c5f245bc1c0f6197638e4608b7fe71e7eb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213499"
---
# <a name="command-line-warning-d9043"></a>Advertencia de la línea de comandos D9043

valor no válido 'nivel_advertencia' para 'compiler_option'; se supone '4999'; Advertencias de análisis de código no están asociadas con niveles de advertencia

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C9043.

```
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```