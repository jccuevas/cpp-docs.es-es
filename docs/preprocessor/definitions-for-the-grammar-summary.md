---
title: Las definiciones del resumen de la gramática | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c11f2f839ef806d74eae65c9fc8fe3a71cd2e9c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760824"
---
# <a name="definitions-for-the-grammar-summary"></a>Definiciones del resumen de la gramática

Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.

Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los elementos no terminales siguientes se definen en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*:

`constant`, *expresión-constante*, *identificador*, *palabra clave*, `operator`, `punctuator`

Un componente opcional se indica mediante el subíndice <sub>opt</sub>. Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:

**{** *expresión*<sub>opt</sub> **}**

## <a name="see-also"></a>Vea también

[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)