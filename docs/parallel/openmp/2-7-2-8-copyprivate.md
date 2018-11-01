---
title: 2.7.2.8 copyprivate
ms.date: 11/04/2016
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
ms.openlocfilehash: d4df1b4216014d3cd15be1480d2f83334fddb72d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622916"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

El **copyprivate** cláusula proporciona un mecanismo para usar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al que proporciona este tipo de variable compartida puede ser difícil (por ejemplo, en una necesidad de una variable diferente en cada nivel de recursividad). El **copyprivate** cláusula solamente puede aparecer en el **único** directiva.

La sintaxis de la **copyprivate** cláusula es como sigue:

```

copyprivate(
variable-list
)

```

El efecto de la **copyprivate** cláusula en una de las variables en su lista de variables que se produce después de la ejecución del bloque estructurado asociado con el **único** construir y antes de cualquiera de los subprocesos en la equipo han dejado la barrera al final de la construcción. A continuación, en todos los demás subprocesos en el equipo de cada variable en el *lista de variables*, esa variable queda definida (como si de asignación) con el valor de la correspondiente estructurado de variable en el subproceso que ejecutó la construcción bloque.

Restricciones para el **copyprivate** cláusula son los siguientes:

- Una variable que se especifica en el **copyprivate** cláusula no debe aparecer en un **privada** o **firstprivate** cláusula para el mismo **único**directiva.

- Si un **único** la directiva con un **copyprivate** cláusula se encuentra en la extensión dinámica de una región paralela, todas las variables que se especifica en el **copyprivate** cláusula debe de forma privada en el contexto envolvente.

- Una variable que se especifica en el **copyprivate** cláusula debe tener un operador de asignación de copia no ambigua accesible.