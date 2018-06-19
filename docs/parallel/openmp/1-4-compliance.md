---
title: 1.4 cumplimiento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1bde41491f456ff99b0cd0d1ccc8ab98508412
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687236"
---
# <a name="14-compliance"></a>1.4 Conformidad
Es una implementación de la API de C o C++ OpenMP *compatible con OpenMP* si lo reconoce y conserva la semántica de todos los elementos de esta especificación, tal y como se disponen en los capítulos 1, 2, 3, 4, y apéndice C. apéndices A, B, D, E y F son para información solo con fines y no forman parte de la especificación. Las implementaciones que incluyan solo un subconjunto de la API no son compatibles con OpenMP.  
  
 La API de C++ y OpenMP C es una extensión para el idioma básico que sea compatible con una implementación. Si el idioma base no es compatible con una construcción de lenguaje o la extensión que aparece en este documento, la implementación de OpenMP no es necesario para admitirla.  
  
 Todas las funciones integradas y funciones de biblioteca estándar de C y C++ (es decir, las funciones que el compilador tiene un conocimiento específico) debe ser seguro para subprocesos. Uso no sincronizado de funciones de subprocesos en subprocesos diferentes dentro de una región paralela no produce un comportamiento indefinido. Sin embargo, el comportamiento puede no ser el mismo que en una región de la serie. (Una función de generación de números aleatorios es un ejemplo).  
  
 La API de C o C++ OpenMP especifica que es cierto comportamiento *definido por la implementación.* Una implementación de OpenMP conforme se requiere para definir y documentar su comportamiento en estos casos. Vea [Apéndice E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), página 97, para obtener una lista de comportamientos definidos por la implementación.