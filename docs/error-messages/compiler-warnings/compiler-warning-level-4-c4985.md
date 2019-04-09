---
title: Advertencia del compilador (nivel 4) C4985
ms.date: 11/04/2016
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 73abb166910cc421f042d22d67efc122e416bceb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024444"
---
# <a name="compiler-warning-level-4-c4985"></a>Advertencia del compilador (nivel 4) C4985

'symbol name': atributos no presentes en la declaración anterior.

Las anotaciones de lenguaje de anotación de código fuente (SAL) de Microsoft en la definición o declaración de método actual se diferencian de las anotaciones en una declaración anterior. Las mismas anotaciones SAL deben usarse en la definición y las declaraciones de un método.

El lenguaje SAL proporciona un conjunto de anotaciones que puede usar para describir la forma en que una función usa sus parámetros, las hipótesis que realiza sobre estos y las garantías que ofrece al final. Las anotaciones se definen en el archivo de encabezado sal.h.

Observe que las macros SAL no se expandirán a menos que el proyecto tenga el marcador [/analyze](../../build/reference/analyze-code-analysis.md) especificado. Si especifica **/analyze**, el compilador puede generar la advertencia C4985, aunque ningún error o advertencia apareciese sin **/analyze**.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Use las mismas anotaciones SAL en la definición de un método y en todas sus declaraciones.

## <a name="see-also"></a>Vea también

[Anotaciones de SAL](../../c-runtime-library/sal-annotations.md)