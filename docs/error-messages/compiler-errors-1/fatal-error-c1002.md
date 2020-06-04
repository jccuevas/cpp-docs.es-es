---
title: Error irrecuperable C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204937"
---
# <a name="fatal-error-c1002"></a>Error irrecuperable C1002

el compilador no tiene espacio en el montón en el paso 2

El compilador se quedó sin espacio de memoria dinámica durante su segundo paso, probablemente debido a un programa con demasiados símbolos o expresiones complejas.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Divida el archivo de origen en varios archivos más pequeños.

1. Divida expresiones en subexpresiones más pequeñas.

1. Quite otros programas o controladores que consuman memoria.
