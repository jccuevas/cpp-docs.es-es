---
title: inline_recursion (Pragma)
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220953"
---
# <a name="inline_recursion-pragma"></a>inline_recursion (Pragma)

Controla la expansión en línea de llamadas de función directas o mutuamente recursivas.

## <a name="syntax"></a>Sintaxis

> **#pragma inline_recursion (** [{ **on** | **OFF** }] **)**

## <a name="remarks"></a>Comentarios

Use esta pragma para controlar las funciones marcadas como [inline](../cpp/inline-functions-cpp.md) [e _ _ inline o](../cpp/inline-functions-cpp.md) funciones que el compilador expande automáticamente bajo la `/Ob2` opción. El uso de esta pragma requiere un valor de la opción del compilador [/OB](../build/reference/ob-inline-function-expansion.md) de 1 o 2. El estado predeterminado de **inline_recursion** es OFF. Esta pragma surte efecto en la primera llamada de función después de que se vea la Directiva pragma y no afecte a la definición de la función.

La Directiva pragma **inline_recursion** controla cómo se expanden las funciones recursivas. Si **inline_recursion** está desactivado y una función insertada se llama a sí misma, ya sea directa o indirectamente, la función se expande solo una vez. Si **inline_recursion** es on, la función se expande varias veces hasta que alcanza el valor establecido con la pragma [inline_depth](../preprocessor/inline-depth.md) , el valor predeterminado para las funciones recursivas que define la `inline_depth` pragma o un límite de capacidad.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (Expansión de funciones insertadas)](../build/reference/ob-inline-function-expansion.md)
