---
title: Error irrecuperable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457786"
---
# <a name="fatal-error-c1126"></a>Error irrecuperable C1126

'identifier': la asignación automática supera el tamaño

Espacio asignado para las variables locales de una función (más una cantidad limitada de espacio utilizado por el compilador, por ejemplo, 20 bytes adicionales para funciones intercambiables) supera el límite.

Para corregir este error, utilice `malloc` o `new` asignar grandes cantidades de datos.