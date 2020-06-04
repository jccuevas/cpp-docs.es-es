---
title: Error irrecuperable C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: c349c09b4931c0a303e7619b364ab237394bd4fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204456"
---
# <a name="fatal-error-c1055"></a>Error irrecuperable C1055

límite del compilador: no hay claves

El archivo de código fuente contiene demasiados símbolos. El compilador se quedó sin claves hash para la tabla de símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Divida el archivo de origen en archivos más pequeños.

1. Elimine los archivos de encabezado innecesarios.

1. Reutilice variables temporales y globales en lugar de crear otras nuevas.
