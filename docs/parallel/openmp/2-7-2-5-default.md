---
title: 2.7.2.5 predeterminado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c054c7f0ac7d1d73768d84613524afc979fecaa5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="2725-default"></a>2.7.2.5 default
El **predeterminado** cláusula permite al usuario que afecta a los atributos de uso compartido de datos de variables. La sintaxis de la **predeterminado** cláusula es como sigue:  
  
```  
default(shared | none)  
```  
  
 Especificar **default(shared)** equivale a enumerar explícitamente cada variable visible en ese momento en un **compartido** cláusula, a menos que sea **threadprivate** o **inconvenientes**`t`-completo. En ausencia de explícito **predeterminado** cláusula, el comportamiento predeterminado es el mismo que if **default(shared)** se especificaron.  
  
 Especificar **default (None)** requiere que al menos uno de los siguientes debe ser true para todas las referencias a una variable de la extensión de la construcción paralela léxica:  
  
-   La variable se muestra explícitamente en una cláusula de atributo de uso compartido de datos de una construcción que contiene la referencia.  
  
-   La variable se declara dentro de la construcción paralela.  
  
-   La variable es **threadprivate**.  
  
-   La variable tiene un **const**-calificado tipo.  
  
-   La variable es la variable de control de bucle para un **para** bucle que sigue inmediatamente a un **para** o **for paralelos** directiva y la referencia de variable aparece dentro del bucle .  
  
 Especificar una variable en un **firstprivate**, **lastprivate**, o **reducción** cláusula de una directiva adjunta hace una referencia implícita a la variable en la envolvente contexto. Tales referencias implícitas también están sujetos a los requisitos mencionados anteriormente.  
  
 Solo una **predeterminado** cláusula se puede especificar en una **paralelo** directiva.  
  
 Predeterminado de una variable atributos de uso compartido de datos se pueden invalidar mediante la **privada**, **firstprivate**, **lastprivate**, **reducción**, y **compartido** cláusulas, como se muestra en el ejemplo siguiente:  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```