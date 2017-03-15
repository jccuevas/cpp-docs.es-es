---
title: "2.7.2.1 private | Microsoft Docs"
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
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.1 private
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La cláusula de `private` declara las variables en variable\-lista que es confidencial a cada subproceso en un equipo.  La sintaxis de la cláusula de `private` es la siguiente:  
  
```  
private(variable-list)  
```  
  
 El comportamiento de la variable especificada en una cláusula de `private` es la siguiente.  Un nuevo objeto con la duración automática de almacenamiento se asigna para la construcción.  El tamaño y alineación de nuevo objeto vienen determinados por el tipo de la variable.  Esta asignación se produce una vez para cada subproceso del equipo, y se invoca un constructor predeterminado para un objeto de clase en caso necesario; si no el valor inicial es indeterminado.  El objeto original al que hace referencia la variable hace un valor indeterminado sobre la entrada a la construcción, no modificar dentro de la extensión dinámica de la construcción, y tiene un valor indeterminado sobre el resultado de la construcción.  
  
 En la extensión léxica de construcción directiva, la variable hace referencia al nuevo objeto privado asignado por el subproceso.  
  
 Restricciones de la cláusula de `private` son los siguientes:  
  
-   Una variable con un tipo de clase que se especifica en una cláusula de `private` debe tener un constructor predeterminado accesible, inequívoca.  
  
-   La variable especificada en una cláusula de `private` no debe tener **const**\- tipo calificado a menos que tenga un tipo de clase con un miembro de `mutable` .  
  
-   La variable especificada en una cláusula de `private` no debe tener un tipo incompleto o un tipo de referencia.  
  
-   Las variables que aparecen en la cláusula de `reduction` de una directiva de **Paralelo** no se pueden especificar en una cláusula de `private` en una directiva de división del trabajo que se enlaza a la construcción paralela.