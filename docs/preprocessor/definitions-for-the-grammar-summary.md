---
title: Definiciones del resumen de la gramática
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 133000c0cc8ef636a3f9752d2f6fc7f1934bd831
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521131"
---
# <a name="definitions-for-the-grammar-summary"></a>Definiciones del resumen de la gramática

Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.

Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los elementos no terminales siguientes se definen en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*:

`constant`, *expresión-constante*, *identificador*, *palabra clave*, `operator`, `punctuator`

Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)