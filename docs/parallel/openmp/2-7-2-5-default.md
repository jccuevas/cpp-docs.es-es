---
title: 2.7.2.5 default
ms.date: 11/04/2016
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
ms.openlocfilehash: efb10913b74ebfae37c95d057955c87bdcfca9a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580256"
---
# <a name="2725-default"></a>2.7.2.5 default

El **predeterminada** cláusula permite al usuario que afectan a los atributos de uso compartido de datos de variables. La sintaxis de la **predeterminada** cláusula es como sigue:

```
default(shared | none)
```

Especificar **default(shared)** es equivalente a enumerar explícitamente cada variable visible actualmente en un **compartido** cláusula, a menos que sea **threadprivate** o **desventajas**`t`-completo. En ausencia de explícita **predeterminada** cláusula, el comportamiento predeterminado es el mismo que if **default(shared)** se han especificado.

Especificar **default (None)** requiere al menos uno de los siguientes debe ser true para todas las referencias a una variable de la extensión léxica de la construcción paralela:

- La variable se muestra explícitamente en una cláusula de atributos de uso compartido de datos de una construcción que contiene la referencia.

- La variable se declara dentro de la construcción paralela.

- La variable es **threadprivate**.

- La variable tiene un **const**-calificado de tipo.

- La variable es la variable de control de bucle para un **para** bucle que sigue inmediatamente a un **para** o **paralelas para** directiva y la referencia de variable aparece dentro del bucle .

Especificar una variable en un **firstprivate**, **lastprivate**, o **reducción** cláusula de una directiva delimitada hace una referencia implícita a la variable en la envolvente contexto. Estas referencias implícitas también están sujetos a los requisitos mencionados anteriormente.

Una sola **predeterminada** cláusula se puede especificar en una **paralelo** directiva.

Predeterminado de una variable se puede invalidar el atributo de uso compartido de datos mediante el uso de la **privada**, **firstprivate**, **lastprivate**, **reducción**, y **compartido** cláusulas, como se muestra en el ejemplo siguiente:

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```