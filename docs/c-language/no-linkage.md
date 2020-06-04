---
title: Sin vinculación
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232394"
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
