---
title: Error del compilador C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603416"
---
# <a name="compiler-error-c2220"></a>Error del compilador C2220

advertencia tratada como error - no se ha generado ningún archivo objeto

[/WX](../../build/reference/compiler-option-warning-level.md) indica al compilador que trate todas las advertencias como errores. Debido a que se ha producido un error, no se ha generado ningún archivo objeto o ejecutable.

Este error solo aparece cuando el **/WX** marca está establecida y se produce una advertencia durante la compilación. Para corregir este error, debe eliminar cada advertencia en el proyecto.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Para corregirlo, use una de las técnicas siguientes

- Corregir los problemas que producen advertencias en el proyecto.

- Compilar en un nivel de advertencia inferior, por ejemplo, usar **/w3** en lugar de **/W4**.

- Use un [advertencia](../../preprocessor/warning.md) pragma para deshabilitar o suprimir una advertencia concreta.

- No use **/WX** para compilar.