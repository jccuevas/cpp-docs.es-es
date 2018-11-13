---
title: Vinculación interna
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 857badd1284378a066c6c19c7159c1535e313593
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452371"
---
# <a name="internal-linkage"></a>Vinculación interna

Si la declaración de un identificador de ámbito de archivo para un objeto o una función contiene el *storage-class-specifier* **static**, el identificador tiene vinculación interna. De lo contrario, el identificador tiene vinculación externa. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) si desea una descripción del elemento no terminal *storage-class-specifier*.

Dentro de una unidad de traducción, cada instancia de un identificador con vinculación interna denota el mismo identificador o función. Los identificadores vinculados internamente son exclusivos para una unidad de traducción.

## <a name="see-also"></a>Vea también

[Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)