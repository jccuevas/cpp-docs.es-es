---
title: "1.2 definición de términos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab188c32c633092efc562d0432ebb7c5662b5ff8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="12-definition-of-terms"></a>1.2 Definición de términos
Los siguientes términos se usan en este documento:  
  
 barrier  
 Un punto de sincronización que debe tener acceso todos los subprocesos de un equipo.  Cada subproceso esperará hasta que todos los subprocesos en el equipo lleguen en este momento. Existen obstáculos explícitos identificados por directivas y barreras implícita creadas por la implementación.  
  
 construct  
 Una construcción es una instrucción. Se compone de una directiva y el bloque estructurado posterior. Tenga en cuenta que algunas directivas no forman parte de una construcción. (Consulte *directiva de openmp* en [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).  
  
 directiva  
 C o C++ **#pragma** seguido por el **omp** identificador, otro texto y una nueva línea. La directiva especifica el comportamiento del programa.  
  
 extensión dinámica  
 Todas las instrucciones en el *extensión léxico*, además de cualquier instrucción dentro de una función que se ejecuta como resultado de la ejecución de instrucciones incluidas en la extensión léxica. Una extensión dinámica también se conoce como un *región*.  
  
 extensión léxico  
 Instrucciones léxicamente incluidas en un *bloque estructurado*.  
  
 subproceso principal  
 El subproceso que se crea un equipo cuando un *región paralela* se escribe.  
  
 región paralela  
 Instrucciones que enlazar a una construcción paralela OpenMP y se pueden ejecutar varios subprocesos.  
  
 private  
 Una variable privada designa un bloque de almacenamiento que sea único en el subproceso que hace la referencia. Tenga en cuenta que hay varias maneras de especificar que una variable es privada: una definición dentro de una región paralela, un **threadprivate** directiva, un **privada**, **firstprivate**, **lastprivate**, o **reducción** cláusula, o el uso de la variable como una **para**variable de control de bucle en una **para** bucles inmediatamente después de un **para** o **for paralelos** directiva.  
  
 región  
 Una extensión dinámica.  
  
 región de serie  
 Las instrucciones ejecutadas únicamente por la *maestro subproceso* fuera de la extensión dinámica de cualquier *región paralela*.  
  
 Serializar  
 Para ejecutar una construcción paralela con un grupo de subprocesos que consta de un único subproceso (que es el subproceso principal para esa construcción paralela), con serie orden de ejecución de las instrucciones dentro del bloque estructurado (el mismo pedido como si el bloque no eran parte de una construcción paralela) y con ningún efecto en el valor devuelto por **omp_in_parallel()** (además de los efectos de cualquier anidada construcciones paralelas).  
  
 shared  
 Una variable compartida nombres de un único bloque de almacenamiento. Todos los subprocesos en un equipo que tienen acceso a esta variable tendrá acceso a este único bloque de almacenamiento.  
  
 bloque estructurado  
 Un bloque estructurado es una instrucción (simples o compuesta) que tiene una sola entrada y una salida única. Ninguna instrucción es un bloque estructurado si hay un salto dentro o fuera de esa instrucción (incluida una llamada a **longjmp**(3C) o el uso de **throw**, pero una llamada a **salir** se permite). Una instrucción compuesta es un bloque estructurado si su ejecución siempre empieza en la apertura **{** y siempre termina en el cierre **}**. Una instrucción de expresión, la instrucción de selección, la instrucción de iteración, o **intente** bloque es un bloque estructurado si obtiene la correspondiente instrucción compuesta incluyendo en **{** y **}** sería un bloque estructurado. Una instrucción de salto, una instrucción con etiqueta o una instrucción de declaración no es un bloque estructurado.  
  
 Equipo  
 Uno o varios subprocesos cooperar en la ejecución de una construcción.  
  
 subproceso  
 Una entidad de ejecución con un flujo de control serie, un conjunto de variables privadas y el acceso a las variables compartidas.  
  
 variable  
 Un identificador, calificado opcionalmente con espacios de nombres, designa un objeto.