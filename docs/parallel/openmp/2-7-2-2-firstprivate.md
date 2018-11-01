---
title: 2.7.2.2 firstprivate
ms.date: 11/04/2016
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
ms.openlocfilehash: f981c66fd3e0a2f42dcf731954f5054f96ed2973
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605977"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

El **firstprivate** cláusula ofrece un superconjunto de la funcionalidad proporcionada por el **privada** cláusula. La sintaxis de la **firstprivate** cláusula es como sigue:

```
firstprivate(variable-list)
```

Las variables especificadas en *lista de variables* tiene **privada** semántica de cláusula, como se describe en [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25. Se produce la inicialización o la construcción como si se lleva a cabo una vez por subproceso, antes de la ejecución del subproceso de la construcción. Para un **firstprivate** cláusula en una construcción paralela, el valor inicial del nuevo objeto privado es el valor del objeto original que existe inmediatamente antes de la construcción paralela para el subproceso que se encuentra. Para un **firstprivate** cláusula en una construcción de uso compartido, el valor inicial del nuevo objeto para cada subproceso que ejecuta la construcción de uso compartido privado es el valor del objeto original que existe antes del punto en el tiempo que el mismo subproceso encuentra la construcción de uso compartido. Además, para los objetos de C++, el nuevo objeto privado para cada subproceso está copiado a partir del objeto original.

Las restricciones para el **firstprivate** cláusula son los siguientes:

- Una variable especificada en un **firstprivate** cláusula no debe tener un tipo incompleto ni un tipo de referencia.

- Una variable con un tipo de clase que se especifica como **firstprivate** debe tener un constructor de copias sea accesible y no ambigua.

- Las variables que son privadas dentro de una región paralela o que aparecen en la **reducción** cláusula de un **paralelo** directiva no se puede especificar en un **firstprivate** cláusula en una Directiva de uso compartido que se enlaza a la construcción paralela.