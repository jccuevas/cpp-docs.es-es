---
title: Advertencia del compilador (nivel 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: 0f8e66982192f8af6498c9151d32a44226e0560a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487781"
---
# <a name="compiler-warning-level-4-c4710"></a>Advertencia del compilador (nivel 4) C4710

'function': función no está entre línea

La función especificada se ha seleccionado para la expansión en línea, pero el compilador no llevó a cabo la inserción.

La inserción se realiza a discreción del compilador. El **inline** palabra clave, como el **registrar** palabra clave, se utiliza como una sugerencia para el compilador. El compilador usa la heurística para determinar si debe insertar una función concreta para acelerar el código al compilar para acelerar el proceso, o si debe insertar una función concreta para reducir el código al compilar para el espacio. El compilador incluirá solo funciones muy pequeñas al compilar para el espacio.

En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Consulte [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de motivos por los que el compilador no alinea una función.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.