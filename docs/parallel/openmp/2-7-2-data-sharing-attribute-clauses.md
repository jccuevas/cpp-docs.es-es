---
title: 2.7.2 cláusulas de atributos de datos compartidos | Microsoft Docs
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
ms.openlocfilehash: 4b8c53cace8d50f10fe638ea8604c46e457f69ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392533"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Cláusulas de atributos de uso compartido de datos

Varias directivas aceptan las cláusulas que permitir que un usuario controlar los atributos de uso compartido de las variables de la duración de la región. Cláusulas de atributos de uso compartido sólo se aplican a las variables de la extensión léxica de la directiva en el que aparece la cláusula. Todas las cláusulas siguientes no se permiten en todas las directivas. La lista de cláusulas que son válidos en una directiva determinada se describen con la directiva.

Si una variable es visible cuando un paralelo o se encuentra la construcción de uso compartido y la variable no se especifica en una cláusula de atributos de uso compartido o **threadprivate** la directiva, a continuación, la variable se comparte. Las variables estáticas declaradas dentro de la extensión dinámica de una región paralela se comparten. Montón de memoria asignada (por ejemplo, mediante **usar malloc()** en C o C++ o la **nuevo** operador en C++) se comparte. (El puntero a esta memoria, sin embargo, puede ser privados o compartidos.) Las variables con una duración de almacenamiento automática declarados dentro de la extensión de una región paralela dinámica son privadas.

La mayoría de las cláusulas de acepta un *lista de variables* argumento, que es una lista separada por comas de variables que están visibles. Si hace referencia una variable en una cláusula de atributos de uso compartido de datos tiene un tipo derivado de una plantilla y no hay ninguna otra referencia a esa variable en el programa, el comportamiento es indefinido.

Todas las variables que aparecen en las cláusulas de la Directiva deben estar visibles. Se pueden repetir las cláusulas según sea necesario, pero no hay ninguna variable puede especificarse en más de una cláusula, salvo que se puede especificar una variable en ambos un **firstprivate** y un **lastprivate** cláusula.

Las secciones siguientes describen las cláusulas de atributos de uso compartido de datos:

- **privada**, [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25.

- **firstprivate**, [sección 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) en página 26.

- **lastprivate**, [sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en página 27.

- **compartido**, [sección 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) en página 27.

- **valor predeterminado**, [sección 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) en la página 28.

- **reducción**, [sección 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) en la página 28.

- **copyin**, [sección 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) página 31.

- **copyprivate**, [sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32.