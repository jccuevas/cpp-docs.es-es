---
title: Error irrecuperable C1055 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6960d8168bd818e4d1baa30e5e54940e6e4dc2e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115455"
---
# <a name="fatal-error-c1055"></a>Error irrecuperable C1055

límite del compilador: no hay claves

El archivo de origen contiene demasiados símbolos. El compilador se quedó sin claves hash para la tabla de símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Dividir el archivo de origen en archivos más pequeños.

1. Elimine los archivos de encabezado innecesarios.

1. Volver a usar las variables temporales y globales en lugar de crear otros nuevos.