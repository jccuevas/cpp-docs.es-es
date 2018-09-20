---
title: 1.3 modelo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c284563a47d21abc9a1dacf045238449d64205d5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394015"
---
# <a name="13-execution-model"></a>1.3 Modelo de ejecución

OpenMP usa el modelo de bifurcar-recombinar de ejecución en paralelo. Aunque este modelo bifurcar-recombinar puede ser útil para solucionar diversos problemas, algo ha sido diseñada para aplicaciones basadas en matrices de gran tamaño. OpenMP está pensado para la compatibilidad con programas que se ejecutarán correctamente tanto como paralelo programas (varios subprocesos de ejecución y una biblioteca de compatibilidad con OpenMP completa) y como programas secuenciales (las directivas que se omiten y una sencilla biblioteca de códigos auxiliares de OpenMP). Sin embargo, es posible y permiten desarrollar un programa que no se comporta correctamente cuando se ejecutan secuencialmente. Además, diferentes grados de paralelismo pueden generar resultados numéricos diferentes debido a cambios en la asociación de las operaciones numéricas. Por ejemplo, una reducción de la adición de serie puede tener un patrón diferente de las asociaciones de adición de una reducción en paralelo. Estas asociaciones diferentes pueden cambiar los resultados de la adición de punto flotante.

Un programa escrito con la API de C/C ++ OpenMP comienza la ejecución como un único subproceso de ejecución llama a la *dominar subproceso*. El subproceso principal se ejecuta en una región de la serie hasta que se encuentra la primera construcción paralela. En la API de C/C ++ OpenMP, el **paralelo** Directiva constituye una construcción paralela. Cuando se encuentra una construcción paralela, el subproceso principal crea un grupo de subprocesos y el maestro se convierte en principal del equipo. Cada subproceso en el equipo ejecuta las instrucciones de la extensión dinámica de una región paralela, excepto para las construcciones de uso compartido. Construcciones de uso compartido se deben encontrar todos los subprocesos en el equipo en el mismo orden y se ejecutan las instrucciones dentro del bloque estructurado asociado por uno o varios de los subprocesos. La barrera implicada al final de una construcción de uso compartido sin una `nowait` cláusula se ejecuta todos los subprocesos en el equipo.

Si un subproceso modifica un objeto compartido, afecta a no solo su propio entorno de ejecución, sino también los de los otros subprocesos del programa. La modificación se garantiza que se complete, desde el punto de vista de uno de los subprocesos, en el siguiente punto de secuencia (como se define en el idioma base) solo si el objeto se declara como volátil. En caso contrario, se garantiza que la modificación que se complete después de la modificación de subproceso en primer lugar, y, a continuación, (o al mismo tiempo) los demás subprocesos, encontrar un **vaciar** directiva que especifica el objeto (implícita o explícitamente). Tenga en cuenta que, cuando el **vaciar** directivas que están implícitos en otras directivas de OpenMP no son suficientes para garantizar el orden deseado de efectos secundarios, es responsabilidad del programador para suministrar adicionales, explícita  **Vaciar** directivas.

Una vez completada la construcción paralela, para sincronizar los subprocesos en el equipo a una barrera implícita y sólo el subproceso principal continúa la ejecución. Cualquier número de construcciones paralelas se puede especificar en un único programa. Como resultado, un programa puede bifurcar y combinar de muchas veces durante la ejecución.

La API de OpenMP C/C ++ permite a los programadores usar directivas de las funciones ejecutadas desde dentro de construcciones paralelas. Se llama a las directivas que no aparecen en la extensión léxica de una construcción paralela, pero es posible que se encuentran en la extensión dinámica *huérfanos* directivas. Directivas huérfanas proporcionan a los programadores la capacidad para ejecutar las partes importantes de su programa en paralelo con los cambios son mínimos para el programa secuencial. Con esta funcionalidad, los usuarios pueden codificar construcciones paralelas en niveles superiores del árbol de llamadas de sistema y use directivas para controlar la ejecución de cualquiera de las funciones llamadas.

Es posible que las funciones que escriben en el mismo archivo de salida en que los datos escritos por diferentes subprocesos aparecen en orden no determinista de salida de llamadas no sincronizadas para C y C++. De forma similar, no sincronizadas las llamadas a funciones que leen el mismo archivo de entrada pueden leer datos en un orden no determinista. Uso no sincronizada de E/S, que cada subproceso tiene acceso a un archivo diferente, genera los mismos resultados que la ejecución en serie de las funciones de E/S.