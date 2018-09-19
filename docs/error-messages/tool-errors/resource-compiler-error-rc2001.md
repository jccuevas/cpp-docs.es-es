---
title: RC2001 de Error del compilador de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75d0f906ba0d7be75ca5177bc1f58bccd226251
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039977"
---
# <a name="resource-compiler-error-rc2001"></a>Error del compilador de recursos RC2001

nueva línea en constante

Una constante de cadena continuó en una segunda línea sin una barra diagonal inversa (**\\**) o de apertura y cierre entre comillas dobles (**"**).

Para interrumpir una constante de cadena que se encuentra en dos líneas en el archivo de origen, realice una de las siguientes acciones:

- La primera línea con el carácter de continuación de línea, una barra diagonal inversa final.

- La cadena en la primera línea con comillas dobles de cierre y abra la cadena en la línea siguiente con otra comilla.

No es suficiente finalizar la primera línea con \n, la secuencia de escape para incrustar un carácter de nueva línea en una constante de cadena.