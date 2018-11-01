---
title: Usar operadores de extracción
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 1fc6ffd2f033dfe3df60260f734d93b79d6824f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626231"
---
# <a name="using-extraction-operators"></a>Usar operadores de extracción

El operador de extracción (`>>`), que está preprogramado para todos los tipos de datos estándar de C++, es la forma más sencilla de obtener los bytes de un objeto de flujo de entrada.

Los operadores de extracción de entrada de texto con formato dependen del espacio en blanco para separar los valores de datos entrantes. Esto es un problema cuando un campo de texto contiene varias palabras o números separados por comas. En ese caso, una alternativa es usar la función miembro de entrada sin formato [istream::getline](../standard-library/basic-istream-class.md#getline) para leer un bloque de texto con espacios en blanco incluidos y, después, analizar el bloque con funciones especiales. Otro método consiste en derivar una clase de flujo de entrada con una función miembro como `GetNextToken`, que puede llamar a los miembros de istream para extraer y dar formato a los datos de caracteres.

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)<br/>
