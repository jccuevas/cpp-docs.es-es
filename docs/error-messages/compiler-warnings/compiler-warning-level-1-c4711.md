---
title: Advertencia del compilador (nivel 1) C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: 9e2adf3583012a670f936c2b86a9ddc393fe53c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175342"
---
# <a name="compiler-warning-level-1-c4711"></a>Advertencia del compilador (nivel 1) C4711

función 'función' seleccionada para expansión en línea

El compilador realizó la inserción en línea en la función especificada, aunque no se marcó para la inserción.

C4711 se habilita si se especifica [/OB2](../../build/reference/ob-inline-function-expansion.md) .

La inserción se realiza a discreción del compilador. Esta advertencia es informativa.

De forma predeterminada, esta advertencia está desactivada. Para habilitar una advertencia, use [#pragma ADVERTENCIA](../../preprocessor/warning.md). Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.
