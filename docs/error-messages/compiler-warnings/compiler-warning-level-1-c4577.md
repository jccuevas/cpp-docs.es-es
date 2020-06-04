---
title: ADVERTENCIA del compilador C4577
description: ADVERTENCIA del compilador C4577 Descripción y solución.
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810559"
---
# <a name="compiler-warning-level-1-c4577"></a>ADVERTENCIA del compilador (nivel 1) C4577

> ' Except ' se usa sin el modo de control de excepciones especificado; no se garantiza la terminación en la excepción. Especificar/EHsc

El compilador detectó una especificación de C++ `noexcept`, pero no se especificó el control de excepciones estándar. El compilador no es totalmente compatible con el C++ control de excepciones según el estándar, a menos que se especifique la opción del compilador [/EHsc](../../build/reference/eh-exception-handling-model.md) . Para resolver este problema, establezca la opción del compilador **/EHsc** .

Esta advertencia es nueva en Visual Studio 2015 y está desactivada de forma predeterminada. Para obtener más información, vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
