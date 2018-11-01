---
title: Error irrecuperable C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620015"
---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509

límite del compilador: hay demasiados estados de controlador de excepciones en la función 'función'. Simplifique la función

El código supera el límite interno de Estados de controlador de excepciones (32.768 estados).

La causa más común es que la función contiene una expresión compleja de operadores aritméticos y las variables de clase definido por el usuario.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Simplificar expresiones mediante la asignación de subexpresiones comunes a las variables temporales.

1. Divida la función en funciones más pequeñas.