---
title: 2.7.2.7 copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94b4c529b7ad6fd717be1e1dee0edd3ff9ac3ff5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426892"
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