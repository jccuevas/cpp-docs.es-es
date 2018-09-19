---
title: Error del compilador C2220 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4179b396e732ceeea20aeb9428d841a357a6d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051326"
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