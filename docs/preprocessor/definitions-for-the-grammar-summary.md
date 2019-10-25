---
title: Definiciones del resumen de la gramática
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 93cf6ffc5daf53a106c9f15a2289e2b52739d72f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222412"
---
# <a name="definitions-for-the-grammar-summary"></a>Definiciones del resumen de la gramática

Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.

Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los siguientes elementos no terminales se definen en la sección [convenciones léxicas](../cpp/lexical-conventions.md) de la  *C++ referencia del lenguaje*:

*constante*, *constante-expresión*, *identificador*, *palabra clave*, *operador*, *signo de puntuación*

Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C++C/)](../preprocessor/grammar-summary-c-cpp.md)
