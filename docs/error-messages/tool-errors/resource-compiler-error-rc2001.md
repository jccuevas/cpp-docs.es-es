---
title: Error del compilador de recursos RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191733"
---
# <a name="resource-compiler-error-rc2001"></a>Error del compilador de recursos RC2001

nueva línea en constante

Una constante de cadena se continuó en una segunda línea sin una barra diagonal inversa ( **\\** ) ni el cierre y la apertura de comillas dobles ( **"** ).

Para dividir una constante de cadena que se encuentra en dos líneas en el archivo de código fuente, realice una de las acciones siguientes:

- Finaliza la primera línea con el carácter de continuación de línea, una barra diagonal inversa.

- Cierre la cadena de la primera línea con comillas dobles y abra la cadena en la línea siguiente con otra comilla.

No es suficiente finalizar la primera línea con \n, la secuencia de escape para insertar un carácter de nueva línea en una constante de cadena.
