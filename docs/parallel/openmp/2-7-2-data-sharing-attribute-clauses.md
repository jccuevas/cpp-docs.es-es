---
title: 2.7.2 cláusulas de atributos de datos compartidos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecc6efac6e3d7356e51dc0ec57009ca9e5a71890
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691913"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Cláusulas de atributos de uso compartido de datos
Varias directivas aceptan las cláusulas que permiten a un usuario controlar los atributos de uso compartido de variables para la duración de la región. Cláusulas de atributos de uso compartido sólo se aplican a las variables de la extensión de la directiva en el que aparece la cláusula léxica. Todas las cláusulas siguientes no se permiten en todas las directivas. La lista de cláusulas que son válidos en una directiva determinada se describen con la directiva.  
  
 Si una variable es visible cuando un paralelo o se encontró la construcción de uso compartido y no se especifica la variable en una cláusula de atributo de uso compartido o **threadprivate** directivas, a continuación, la variable se comparte. Las variables estáticas declaradas dentro de la extensión dinámica de una región paralela se comparten. Asignada memoria del montón (por ejemplo, si se usa **malloc()** en C o C++ o **nueva** operador en C++) se comparte. (El puntero a esta memoria, sin embargo, puede ser privados o compartidos.) Las variables con una duración de almacenamiento automática declarados dentro de la extensión dinámica de una región paralela son privadas.  
  
 La mayoría de las cláusulas acepte un *lista de variables* argumento, que es una lista separada por comas de variables que están visibles. Si hace referencia una variable en una cláusula de atributo de uso compartido de datos tiene un tipo derivado de una plantilla y no hay ninguna otra referencia a esa variable en el programa, el comportamiento es indefinido.  
  
 Todas las variables que aparecen en cláusulas de la Directiva deben ser visibles. Las cláusulas se pueden repetir según sea necesario, pero no hay ninguna variable puede especificarse en más de una cláusula, salvo que una variable puede especificarse tanto en un **firstprivate** y un **lastprivate** cláusula.  
  
 Las siguientes secciones describen las cláusulas de atributos de uso compartido de datos:  
  
-   **privada**, [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en página 25.  
  
-   **firstprivate**, [sección 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) en página 26.  
  
-   **lastprivate**, [sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en página 27.  
  
-   **compartido**, [sección 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) en página 27.  
  
-   **valor predeterminado**, [sección 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) en página 28.  
  
-   **reducción**, [sección 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) en página 28.  
  
-   **copyin**, [sección 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) en página 31.  
  
-   **copyprivate**, [sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32.