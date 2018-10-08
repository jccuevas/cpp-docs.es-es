---
title: 1.2 definición de términos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66cbf25324b71c3fd28bdd344c7a217348cdb5d9
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861621"
---
# <a name="12-definition-of-terms"></a>1.2 Definición de términos

Los siguientes términos se usan en este documento:

- barrier

   Un punto de sincronización que debe tener acceso a todos los subprocesos en un equipo.  Cada subproceso esperará hasta que todos los subprocesos en el equipo lleguen en este momento. Existen obstáculos explícitos identificados por las directivas e implícitas barreras creadas por la implementación.

- construct

   Una construcción es una instrucción. Consta de una directiva y el bloque estructurado posteriores. Tenga en cuenta que algunas directivas no forman parte de una construcción. (Consulte *directiva de openmp* en [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).

- directiva

   C o C++ **#pragma** seguido por el **omp** identificador, otro texto y una nueva línea. La directiva especifica el comportamiento del programa.

- extensión dinámica

   Todas las instrucciones de la *extensión léxico*, además de cualquier instrucción dentro de una función que se ejecuta como resultado de la ejecución de instrucciones de la extensión léxica. Una extensión dinámica también se conoce como un *región*.

- extensión léxico

   Instrucciones léxicamente dentro un *bloque estructurado*.

- subproceso principal

   El subproceso que crea un equipo cuando un *región paralela* se ha especificado.

- región paralela

   Instrucciones que enlazar a una construcción paralela de OpenMP y se pueden ejecutar varios subprocesos.

- private

   Una variable privada nombres de un bloque de almacenamiento que es único para el subproceso que hace la referencia. Tenga en cuenta que hay varias maneras de especificar que una variable privada: una definición dentro de una región paralela, un **threadprivate** directiva, un **privada**, **firstprivate**, **lastprivate**, o **reducción** cláusula o el uso de la variable como un **para**variable de control de bucle en una **para** bucle inmediatamente después de un **para** o **paralelas para** directiva.

- región

   Una extensión dinámica.

- región de serie

   Las instrucciones ejecutadas únicamente por la *dominar subproceso* fuera de la extensión dinámica de cualquier *región paralela*.

- Serializar

   Para ejecutar una construcción paralela con un grupo de subprocesos que consta de un único subproceso (que es el subproceso principal para esa construcción paralela), con el orden de ejecución para las instrucciones incluidas en el bloque estructurado en serie (el mismo orden como si el bloque no eran parte de una construcción paralela) y no tiene ningún efecto en el valor devuelto por **omp_in_parallel()** (aparte de los efectos de cualquier anidados construcciones paralelas).

- shared

   Una variable compartida nombres de un único bloque de almacenamiento. Todos los subprocesos en un equipo que tienen acceso a esta variable tendrá acceso a este bloque de almacenamiento único.

- bloque estructurado

   Un bloque estructurado es una instrucción (simple o compuesta) que tiene una sola entrada y una salida única. Instrucción no es un bloque estructurado si hay un salto dentro o fuera de esa instrucción (incluidos una llamada a **longjmp**(3C) o el uso de **throw**, pero una llamada a **salir** se permite). Una instrucción compuesta es un bloque estructurado si su ejecución siempre comienza en la apertura **{** y siempre termina en el cierre **}**. Una instrucción de expresión, la instrucción de selección, la instrucción de iteración, o **intente** bloque es un bloque estructurado si obtuvo la correspondiente instrucción compuesta escribiéndolo en **{** y **}** sería un bloque estructurado. Una instrucción de salto, la instrucción con etiqueta o la instrucción de declaración no es un bloque estructurado.

- Equipo

   Uno o varios subprocesos cooperan y cumplen la ejecución de una construcción.

- subproceso

   Una entidad de ejecución tiene un flujo de control serie, un conjunto de variables privadas y el acceso a las variables compartidas.

- variable

   Un identificador, calificado opcionalmente con espacios de nombres, los nombres de un objeto.
