---
title: Error irrecuperable C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: e6df4870d7af49c369be7e513791955599c48326
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636520"
---
# <a name="fatal-error-c1055"></a>Error irrecuperable C1055

límite del compilador: no hay claves

El archivo de origen contiene demasiados símbolos. El compilador se quedó sin claves hash para la tabla de símbolos.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Dividir el archivo de origen en archivos más pequeños.

1. Elimine los archivos de encabezado innecesarios.

1. Volver a usar las variables temporales y globales en lugar de crear otros nuevos.