---
title: Error irrecuperable C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: 0d1d7255dd64239a6a76bb15a1f309b43eac0d4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202961"
---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509

límite del compilador: hay demasiados Estados de controlador de excepciones en la función ' function '. Simplifique la función

El código supera un límite interno en los Estados del controlador de excepciones (Estados 32.768).

La causa más común es que la función contiene una expresión compleja de variables de clase definidas por el usuario y operadores aritméticos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Simplifique las expresiones asignando subexpresiones comunes a las variables temporales.

1. Divida la función en funciones más pequeñas.
