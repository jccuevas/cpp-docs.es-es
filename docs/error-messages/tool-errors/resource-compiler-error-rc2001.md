---
title: Error del compilador de recursos RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602116"
---
# <a name="resource-compiler-error-rc2001"></a>Error del compilador de recursos RC2001

nueva línea en constante

Una constante de cadena continuó en una segunda línea sin una barra diagonal inversa (**\\**) o de apertura y cierre entre comillas dobles (**"**).

Para interrumpir una constante de cadena que se encuentra en dos líneas en el archivo de origen, realice una de las siguientes acciones:

- La primera línea con el carácter de continuación de línea, una barra diagonal inversa final.

- La cadena en la primera línea con comillas dobles de cierre y abra la cadena en la línea siguiente con otra comilla.

No es suficiente finalizar la primera línea con \n, la secuencia de escape para incrustar un carácter de nueva línea en una constante de cadena.