---
title: Error irrecuperable C1126 | Documentos de Microsoft
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
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1126"></a>Error irrecuperable C1126
'identificador': la asignación automática supera el tamaño  
  
 Espacio asignado para las variables locales de una función (más una cantidad limitada de espacio utilizado por el compilador, por ejemplo, 20 bytes adicionales para funciones intercambiables) supera el límite.  
  
 Para corregir este error, utilice `malloc` o `new` para asignar grandes cantidades de datos.