---
title: Advertencia del compilador (nivel 1) C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: c10b19b39fcb40527c9e9276f47ecff42ca5a643
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280391"
---
# <a name="compiler-warning-level-1-c4711"></a>Advertencia del compilador (nivel 1) C4711

función 'función' seleccionada para expansión en línea

El compilador realiza inserción en la función especificada, aunque no se marcó para inserción.

C4711 está habilitada si [/Ob2](../../build/reference/ob-inline-function-expansion.md) se especifica.

La inserción se realiza a discreción del compilador. La advertencia es informativa.

De forma predeterminada, esta advertencia está desactivada. Para habilitar una advertencia, use [advertencia #pragma](../../preprocessor/warning.md). Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.