---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 65bb8faba085e5582e779fa0e9d5bf1a91a39f0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545449"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin

El **copyin** cláusula proporciona un mecanismo para asignar el mismo valor para **threadprivate** variables para cada subproceso en el equipo de ejecución de la región paralela. Para cada variable especificada en un **copyin** cláusula, el valor de la variable en el subproceso principal del equipo de copia, como si la asignación, en las copias de subprocesos privados al principio de la región paralela. La sintaxis de la **copyin** cláusula es como sigue:

```

copyin(
variable-list
)

```

Las restricciones para el **copyin** cláusula son los siguientes:

- Una variable que se especifica en el **copyin** cláusula debe tener un operador de asignación de copia accesible y no ambigua.

- Una variable que se especifica en el **copyin** cláusula debe ser un **threadprivate** variable.