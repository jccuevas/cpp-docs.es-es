---
title: "Las definiciones para el resumen de la gramática | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 755533d59b9b893da4a657db6da2ea80f13138b5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="definitions-for-the-grammar-summary"></a>Definiciones del resumen de la gramática
Los elementos terminales son puntos de conexión en una definición de sintaxis. No hay ninguna otra posible resolución. Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.  
  
Los elementos no terminales son marcadores en la sintaxis. La mayoría se definen en otro lugar en este resumen de la sintaxis. Las definiciones pueden ser recursivas. Los elementos no terminales siguientes se definen en el [convenciones léxicas](../cpp/lexical-conventions.md) sección de la *referencia del lenguaje C++*:  
  
`constant`, *constant-expression*, *identifier*, *keyword*, `operator`, `punctuator`  
  
Un componente opcional se indica mediante el subíndice opt. Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:  
  
**{** *expresión*opt **}**  
  
## <a name="see-also"></a>Vea también  
[Resumen de la gramática (C/C++)](../preprocessor/grammar-summary-c-cpp.md)