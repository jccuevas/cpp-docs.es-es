---
title: "1.3 modelo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce9c2398b38effebbca428c811d86481ca94e7cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="13-execution-model"></a>1.3 Modelo de ejecución
OpenMP usa el modelo de tipo bifurcar-recombinar de ejecución en paralelo. Aunque este modelo del tipo bifurcar-recombinar puede ser útil para resolver diversos problemas, algo ha sido diseñado para aplicaciones basadas en matrices de gran tamaño. OpenMP está destinado a los programas de soporte técnico que se ejecutarán correctamente ambos como paralelo programas (varios subprocesos de ejecución y una biblioteca de compatibilidad con OpenMP completa) y como programas secuenciales (directivas pasa por alto y una biblioteca de código auxiliar de OpenMP simple). Sin embargo, es posible y permiten desarrollar un programa que no se comporten correctamente cuando se ejecutan secuencialmente. Además, diferentes grados de paralelismo pueden generar resultados numéricos diferentes debido a los cambios en la asociación de operaciones numéricas. Por ejemplo, una reducción de adición de serie puede tener un patrón diferente de asociaciones de adición de una reducción en paralelo. Estas asociaciones diferentes pueden cambiar los resultados de la adición de punto flotante.  
  
 Un programa escrito con la API de C o C++ OpenMP comienza la ejecución como un único subproceso de ejecución llama a la *maestro subproceso*. El subproceso principal se ejecuta en una región de serie hasta que se encuentra la primera construcción paralela. En la API de C o C++ OpenMP, el **paralelo** Directiva constituye una construcción paralela. Cuando se encuentra una construcción paralela, el subproceso principal crea un equipo de subprocesos y el maestro se convierte en principal del equipo. Cada subproceso en el equipo ejecuta las instrucciones de la extensión dinámica de una región paralela, excepto las construcciones de uso compartido. Se deben encontrar construcciones de uso compartido por todos los subprocesos en el equipo en el mismo orden y se ejecutan las instrucciones dentro del bloque estructurado asociado por uno o varios de los subprocesos. La barrera implicada al final de una construcción de uso compartido sin una `nowait` cláusula se ejecuta por todos los subprocesos en el equipo.  
  
 Si un subproceso modifica un objeto compartido, afecta a no solo su propio entorno de ejecución, sino también los de los demás subprocesos en el programa. La modificación se garantiza como completada, desde el punto de vista de uno de los subprocesos, en el siguiente punto de secuencia (tal y como se define en el idioma base) solo si el objeto se declara como volátil. En caso contrario, se garantiza que la modificación se completa después de la modificación de subproceso en primer lugar, y, a continuación, (o al mismo tiempo) de los demás subprocesos, encontrar un **vaciar** directiva que especifica el objeto (implícita o explícitamente). Tenga en cuenta que, cuando la **vaciar** directivas que están implícitas por otras directivas de OpenMP no son suficientes para garantizar el orden deseado de los efectos secundarios, es responsabilidad del programador para proporcionar adicionales, explícita  **Vaciar** directivas.  
  
 Tras la finalización de la construcción paralela, sincronizan los subprocesos en el equipo en una barrera implícita y solo el subproceso principal continúa la ejecución. Cualquier número de construcciones paralelas puede especificarse en un único programa. Como resultado, un programa puede bifurcar y combinar muchas veces durante la ejecución.  
  
 La API de C o C++ OpenMP permite a los programadores usar las directivas de las funciones ejecutadas desde dentro de construcciones paralelas. Se llaman a las directivas que no aparecen en la extensión léxica de una construcción paralela, pero pueden haber en la extensión dinámica *huérfanos* directivas. Directivas huérfanas dan a los programadores la capacidad para ejecutar las partes principales de su programa en paralelo con cambios mínimos únicamente al programa secuencial. Con esta funcionalidad, los usuarios pueden codificar construcciones paralelas en niveles superiores del árbol de llamadas de programa y usar las directivas para controlar la ejecución de cualquiera de las funciones llamadas.  
  
 Las llamadas no sincronizadas a C y C++ de salida está penada por las funciones que escriben en el mismo archivo de salida en la que los datos escritos en subprocesos diferentes aparecen en un orden no determinista. De forma similar, no sincronizadas llamadas a funciones que lee desde el mismo archivo de entrada pueden leer datos en un orden no determinista. Uso no sincronizado de E/S, que cada subproceso tiene acceso a un archivo diferente, genera los mismos resultados que la ejecución en serie de las funciones de E/S.