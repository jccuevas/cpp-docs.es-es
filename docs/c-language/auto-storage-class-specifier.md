---
title: auto (Especificador de clase de almacenamiento)
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 926322fa55a14cc736dc41fbebd5c276ad61f020
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619913"
---
# <a name="auto-storage-class-specifier"></a>auto (Especificador de clase de almacenamiento)

El especificador de clase de almacenamiento **auto** declara una variable automática, una variable con una duración local. Una variable **auto** solo es visible en el bloque en que se declara. Las declaraciones de variables **auto** pueden incluir inicializadores, como se describe en [Inicialización](../c-language/initialization.md). Como las variables con clase de almacenamiento **auto** no se inicializan automáticamente, debe inicializarlas explícitamente al declararlas, o bien asignarles valores iniciales en instrucciones dentro del bloque. Los valores de variables **auto** no inicializadas no están definidos. (Una variable local de clase de almacenamiento **auto** o **register** se inicializa cada vez que entra en el ámbito si se proporciona un inicializador).

Una variable **static** interna (una variable static con ámbito local o de bloque) se puede inicializar con la dirección de cualquier elemento externo o **static**, pero no con la dirección de otro elemento **auto**, porque la dirección de un elemento **auto** no es una constante.

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../cpp/auto-keyword.md)