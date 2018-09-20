---
title: 2.7.2.3 lastprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25edca8391eb094691ef4fea3c360d351f979b43
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385968"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

El `lastprivate` cláusula ofrece un superconjunto de la funcionalidad proporcionada por el `private` cláusula. La sintaxis de la `lastprivate` cláusula es como sigue:

```
lastprivate(variable-list)
```

Las variables especificadas en el *lista de variables* tiene `private` semántica de la cláusula. Cuando un `lastprivate` cláusula aparece en la directiva que identifica una construcción de uso compartido, el valor de cada `lastprivate` variable desde la última secuencialmente iteración de bucle asociado o la directiva de léxicamente última sección, se asigna a la objeto original de la variable. Las variables que no se ha asignado un valor la última iteración de la **para** o **paralelas para**, o en la sección del última léxicamente el **secciones** o  **las secciones en paralelo** directiva, tienen valores indeterminados después de la construcción. Sin asignar subobjetos también tienen un valor indeterminado después de la construcción.

Las restricciones para el `lastprivate` cláusula son los siguientes:

- Todas las restricciones para `private` aplicar.

- Una variable con un tipo de clase que se especifica como `lastprivate` debe tener un operador de asignación de copia accesible y no ambigua.

- Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una **paralelo** directiva no se puede especificar en un `lastprivate` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.