---
title: Error irrecuperable C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230017"
---
# <a name="fatal-error-c1126"></a>Error irrecuperable C1126

'identifier': la asignación automática supera el tamaño

Espacio asignado para las variables locales de una función (más una cantidad limitada de espacio utilizado por el compilador, por ejemplo, 20 bytes adicionales para funciones intercambiables) supera el límite.

Para corregir este error, utilice `malloc` o `new` asignar grandes cantidades de datos.