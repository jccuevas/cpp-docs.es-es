---
title: Error irrecuperable C1126 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f014aafc60a36bfbb4edad50e7e3ceede6e3c8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062480"
---
# <a name="fatal-error-c1126"></a>Error irrecuperable C1126

'identifier': la asignación automática supera el tamaño

Espacio asignado para las variables locales de una función (más una cantidad limitada de espacio utilizado por el compilador, por ejemplo, 20 bytes adicionales para funciones intercambiables) supera el límite.

Para corregir este error, utilice `malloc` o `new` asignar grandes cantidades de datos.