---
title: "2.7.2.5 default | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.5 default
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La cláusula de **predeterminado** permite al usuario afecta a los atributos de datos de las variables.  La sintaxis de la cláusula de **predeterminado** es la siguiente:  
  
```  
default(shared | none)  
```  
  
 Especificar **valor predeterminado \(compartido\)** equivale explícitamente a enumerar cada variable actualmente visible en una cláusula de **compartido** , a menos que sea **threadprivate** o **con**`t`\- completo.  En ausencia de una cláusula explícita de **predeterminado** , el comportamiento predeterminado es el mismo que si **valor predeterminado \(compartido\)** fuera especificado.  
  
 Especificar **establezca como valor predeterminado \(ninguno\)** requiere que por lo menos uno de los siguientes debe ser true para cada referencia a una variable en la extensión léxica de construcción paralela:  
  
-   La variable explícitamente aparece en una cláusula de atributo de uso compartido de datos de una construcción que contiene la referencia.  
  
-   la variable se declara dentro de la construcción paralela.  
  
-   la variable es **threadprivate**.  
  
-   La variable tiene **const**\- tipo completo.  
  
-   La variable es la variable de control de bucle para un bucle de **Para** que inmediatamente siga una directiva de **Para** o de **paralelo para** , y la referencia variable aparece dentro del bucle.  
  
 Especificando una variable en **firstprivate**, **lastprivate**, o la cláusula de **informe detallado** de una directiva incluida produce una referencia implícita a la variable en el contexto envolvente.  Dichas referencias implícitas son también bajo los requisitos anteriores.  
  
 Una sola cláusula de **predeterminado** se puede especificar en una directiva de **Paralelo** .  
  
 El atributo predeterminado de uso compartido de datos de una variable se puede reemplazar utilizando **private**, **firstprivate**, **lastprivate**, **informe detallado**, y las cláusulas de **compartido** , tal como se muestra en el ejemplo siguiente:  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```