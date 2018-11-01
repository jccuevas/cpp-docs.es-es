---
title: 1.4 Conformidad
ms.date: 11/04/2016
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
ms.openlocfilehash: 7fb47c9989e971e10701c2ee2bd7ac7823141812
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642460"
---
# <a name="14-compliance"></a>1.4 Conformidad

Es una implementación de la API de OpenMP C/C ++ *OpenMP conforme* si reconoce y conserva la semántica de todos los elementos de esta especificación, como se definen en los capítulos 1, 2, 3, 4, y son Apéndice C. apéndices A, B, D, E y F para información solo con fines y no forman parte de la especificación. Las implementaciones que incluyen solo un subconjunto de la API no son compatibles con OpenMP.

El de OpenMP C y C++ API es una extensión para el idioma base que es compatible con una implementación. Si el idioma base no es compatible con una construcción de lenguaje o la extensión que aparece en este documento, la implementación de OpenMP no es necesario para admitirlo.

Todas las funciones de biblioteca estándar de C y C++ y las funciones integradas (es decir, de que el compilador tiene un conocimiento específico de funciones) debe ser seguro para subprocesos. Uso no sincronizada de funciones de subprocesos que diferentes subprocesos dentro de una región paralela no producir un comportamiento indefinido. Sin embargo, el comportamiento puede no ser igual que en una región de la serie. (Una función de generación de números aleatorios es un ejemplo).

La API de C/C ++ OpenMP especifica que es cierto comportamiento *definido por la implementación.* Una implementación de OpenMP conforme se requiere para definir y documentar su comportamiento en estos casos. Consulte [Apéndice E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), página 97, para obtener una lista de comportamientos definidos en la implementación.