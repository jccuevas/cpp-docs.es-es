---
title: inline_depth (Pragma)
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: be57178280e278683b85db1413ff5724b5260aef
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220984"
---
# <a name="inline_depth-pragma"></a>inline_depth (Pragma)

Especifica la profundidad de búsqueda heurística en línea. Las funciones con una profundidad en el gráfico de llamadas superior al valor especificado no se insertan.

## <a name="syntax"></a>Sintaxis

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>Comentarios

Esta pragma controla la inserción de funciones marcadas como [inline](../cpp/inline-functions-cpp.md) e _ _ inline [, o](../cpp/inline-functions-cpp.md)insertadas `/Ob` automáticamente bajo la opción.

*n* puede ser un valor comprendido entre 0 y 255, donde 255 significa una profundidad ilimitada en el gráfico de llamadas. Un valor de 0 impide la expansión en línea. Cuando no se especifica *n* , se usa el valor predeterminado 254.

La Directiva pragma **inline_depth** controla el número de veces que se puede expandir una serie de llamadas de función. Por ejemplo, supongamos que la profundidad alineada es 4. Si a llama a B y B después llama a C, las tres llamadas se expanden en línea. Sin embargo, si la expansión de profundidad alineada más cercana es 2, solo se expanden A y B, y C permanece como una llamada de función.

Para utilizar esta directiva pragma, debe establecer la `/Ob` opción del compilador en 1 o superior. La profundidad establecida mediante esta directiva pragma surte efecto en la primera llamada a función después de pragma.

La profundidad alineada se puede reducir durante la expansión, pero no aumentar. Si la profundidad alineada es 6 y durante la expansión, el preprocesador encuentra una pragma **inline_depth** con un valor de 8, la profundidad sigue siendo 6.

La Directiva pragma **inline_depth** no tiene ningún efecto en las `__forceinline`funciones marcadas con.

> [!NOTE]
> Las funciones recursivas pueden sustituirse alineadas con una profundidad máxima de 16 llamadas.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
