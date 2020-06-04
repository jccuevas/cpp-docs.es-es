---
title: Advertencia del compilador (nivel 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 82adb80310fb43c848c253f9bf5e436c8c379f35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198100"
---
# <a name="compiler-warning-level-4-c4985"></a>Advertencia del compilador (nivel 4) C4985

'symbol name': atributos no presentes en la declaración anterior.

Las anotaciones de lenguaje de anotación de código fuente (SAL) de Microsoft en la definición o declaración de método actual se diferencian de las anotaciones en una declaración anterior. Las mismas anotaciones SAL deben usarse en la definición y las declaraciones de un método.

El lenguaje SAL proporciona un conjunto de anotaciones que puede usar para describir la forma en que una función usa sus parámetros, las hipótesis que realiza sobre estos y las garantías que ofrece al final. Las anotaciones se definen en el archivo de encabezado sal.h.

Observe que las macros SAL no se expandirán a menos que el proyecto tenga el marcador [/analyze](../../build/reference/analyze-code-analysis.md) especificado. Si especifica **/analyze**, el compilador puede generar la advertencia C4985, aunque ningún error o advertencia apareciese sin **/analyze**.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Use las mismas anotaciones SAL en la definición de un método y en todas sus declaraciones.

## <a name="see-also"></a>Consulte también

[Anotaciones SAL](../../c-runtime-library/sal-annotations.md)
