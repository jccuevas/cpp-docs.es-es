---
title: "Usar operadores de extracción | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extraction operators
- '>> operator, extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: e5dcc1e57b807ee7ff7b4292f31563d4041c0bdd
ms.lasthandoff: 02/24/2017

---
# <a name="using-extraction-operators"></a>Usar operadores de extracción
El operador de extracción (`>>`), que está preprogramado para todos los tipos de datos estándar de C++, es la forma más sencilla de obtener los bytes de un objeto de flujo de entrada.  
  
 Los operadores de extracción de entrada de texto con formato dependen del espacio en blanco para separar los valores de datos entrantes. Esto es un problema cuando un campo de texto contiene varias palabras o números separados por comas. En ese caso, una alternativa es usar la función miembro de entrada sin formato [istream::getline](../standard-library/basic-istream-class.md#basic_istream__getline) para leer un bloque de texto con espacios en blanco incluidos y, después, analizar el bloque con funciones especiales. Otro método consiste en derivar una clase de flujo de entrada con una función miembro como `GetNextToken`, que puede llamar a los miembros de istream para extraer y dar formato a los datos de caracteres.  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)


