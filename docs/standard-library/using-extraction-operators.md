---
title: "Usar operadores de extracción | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb9e62ffd1e466fd220012717e278b79bbce3e1f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="using-extraction-operators"></a>Usar operadores de extracción
El operador de extracción (`>>`), que está preprogramado para todos los tipos de datos estándar de C++, es la forma más sencilla de obtener los bytes de un objeto de flujo de entrada.  
  
 Los operadores de extracción de entrada de texto con formato dependen del espacio en blanco para separar los valores de datos entrantes. Esto es un problema cuando un campo de texto contiene varias palabras o números separados por comas. En ese caso, una alternativa es usar la función miembro de entrada sin formato [istream::getline](../standard-library/basic-istream-class.md#getline) para leer un bloque de texto con espacios en blanco incluidos y, después, analizar el bloque con funciones especiales. Otro método consiste en derivar una clase de flujo de entrada con una función miembro como `GetNextToken`, que puede llamar a los miembros de istream para extraer y dar formato a los datos de caracteres.  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)

