---
title: Error del compilador C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206666"
---
# <a name="compiler-error-c2220"></a>Error del compilador C2220

advertencia tratada como error - no se ha generado ningún archivo objeto

[/WX](../../build/reference/compiler-option-warning-level.md) indica al compilador que trate todas las advertencias como errores. Debido a que se ha producido un error, no se ha generado ningún archivo objeto o ejecutable.

Este error solo aparece cuando se establece la marca **/WX** y se produce una advertencia durante la compilación. Para corregir este error, debe eliminar cada advertencia en el proyecto.

### <a name="to-fix-use-one-of-the-following-techniques"></a>Para corregirlo, use una de las técnicas siguientes

- Corregir los problemas que producen advertencias en el proyecto.

- Compilar en un nivel de advertencia inferior; por ejemplo, use **/W3** en lugar de **/W4**.

- Use una pragma [Warning](../../preprocessor/warning.md) para deshabilitar o suprimir una advertencia concreta.

- No use **/WX** para compilar.
