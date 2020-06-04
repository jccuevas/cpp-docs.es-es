---
title: Advertencia del compilador (nivel 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c39848b9b3e94e35c4d0c0937a0974b717c6bd8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198181"
---
# <a name="compiler-warning-level-4-c4710"></a>Advertencia del compilador (nivel 4) C4710

' función ': la función no está insertada

Se seleccionó la función especificada para la expansión en línea, pero el compilador no realizó la inserción.

La inserción se realiza a discreción del compilador. La palabra clave **inline** , como la palabra clave **Register** , se utiliza como una sugerencia para el compilador. El compilador usa la heurística para determinar si debe alinear una función concreta con el fin de acelerar el código al compilar para obtener velocidad, o si debe alinear una función concreta para reducir el código al compilar el espacio. El compilador solo insertará funciones muy pequeñas al compilar para el espacio.

En algunos casos, el compilador no insertará una función concreta por motivos mecánicos. Vea [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de los motivos por los que el compilador no puede alinear una función.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.
