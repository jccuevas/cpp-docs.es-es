---
title: Definiciones del resumen de la gramática
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 6e8671ba0d68b13f68db0f2b08dab4fe98f917e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389286"
---
# <a name="definitions-for-the-grammar-summary"></a>Definiciones del resumen de la gramática

Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.

Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los elementos no terminales siguientes se definen en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*:

`constant`, *constant-expression*, *identifier*, *keyword*, `operator`, `punctuator`

Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:

**{** *expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)