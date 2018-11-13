---
title: Sin vinculación
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: 9775270c5c1fb0b6758f994c432104d75e19d38d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505084"
---
# <a name="no-linkage"></a>Sin vinculación

Si una declaración de un identificador dentro de un bloque no incluye el especificador de clase de almacenamiento `extern`, el identificador no tiene ninguna vinculación y es exclusivo de la función.

Los identificadores siguientes no tienen vinculación:

- Un identificador declarado como algo distinto de un objeto o función

- Un identificador declarado como un parámetro de función

- Un identificador de ámbito de bloque para un objeto declarado sin el especificador de clase de almacenamiento `extern`

Si un identificador no tiene vinculación, al volver a declararse el mismo nombre (en un especificador de declarador o tipo) en el mismo nivel de ámbito, se genera un error de redefinición de símbolo.

## <a name="see-also"></a>Vea también

[Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)