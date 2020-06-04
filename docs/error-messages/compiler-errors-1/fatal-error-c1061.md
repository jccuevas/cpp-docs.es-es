---
title: Error irrecuperable C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 049adb38dd8f33de7dbdd02d8420eba284ca2ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204417"
---
# <a name="fatal-error-c1061"></a>Error irrecuperable C1061

límite del compilador: los bloques están demasiado anidados

El anidamiento de bloques de código supera el límite de 128 niveles. Se trata un límite estricto del compilador de C y C++, tanto en el conjunto de herramientas de 32 bits y como en el de 64 bits. El número de niveles anidados se puede aumentar por cualquier elemento que cree un ámbito o un bloque. Por ejemplo, espacios de nombres, directivas using, expansiones de preprocesador, expansión de plantilla, control de excepciones, construcciones de bucle y cláusulas else-if que puedan aumentar el nivel de anidamiento en el compilador.

Para corregir este error debe refactorizar el código. En cualquier caso, un código profundamente anidado es difícil entender y analizar. Refactorizar el código para tener menos niveles de anidamiento puede mejorar la calidad del código y simplificar el mantenimiento. Divida el código profundamente anidado en funciones que se invoquen desde el contexto original. Limite el número de bucles o cláusulas else-if anidadas dentro de un bloque.
