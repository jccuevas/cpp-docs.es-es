---
title: ADVERTENCIA del compilador C4577
description: ADVERTENCIA del compilador C4577 Descripción y solución.
ms.date: 09/18/2019
helpviewer_keywords:
- C4577
ms.openlocfilehash: 637023f4c27f93238fbbd13b4a0e652e6cd958e0
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71241130"
---
# <a name="compiler-warning-level-1-c4577"></a>ADVERTENCIA del compilador (nivel 1) C4577

> ' Except ' se usa sin el modo de control de excepciones especificado; no se garantiza la terminación en la excepción. Especificar/EHsc

El compilador `noexcept` detectó una especificación C++ , pero no se especificó el control de excepciones estándar. El compilador no es totalmente compatible con el C++ control de excepciones según el estándar, a menos que se especifique la opción del compilador [/EHsc](../../build/reference/eh-exception-handling-model.md) . Para resolver este problema, establezca la opción del compilador **/EHsc** .

Esta advertencia es nueva en Visual Studio 2015 y está desactivada de forma predeterminada. Para obtener más información, vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
