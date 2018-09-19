---
title: Error irrecuperable C1509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 837ab5b7cf76b724726c6c52fbfe974d4da6ca85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033139"
---
# <a name="fatal-error-c1509"></a>Error irrecuperable C1509

límite del compilador: hay demasiados estados de controlador de excepciones en la función 'función'. Simplifique la función

El código supera el límite interno de Estados de controlador de excepciones (32.768 estados).

La causa más común es que la función contiene una expresión compleja de operadores aritméticos y las variables de clase definido por el usuario.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Simplificar expresiones mediante la asignación de subexpresiones comunes a las variables temporales.

1. Divida la función en funciones más pequeñas.