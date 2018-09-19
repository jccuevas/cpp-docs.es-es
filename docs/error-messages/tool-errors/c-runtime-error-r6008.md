---
title: C Runtime Error R6008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b06566f84003b08f5fe3869a021c4bf86dcf5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105163"
---
# <a name="c-runtime-error-r6008"></a>C Runtime Error R6008

No hay suficiente espacio para los argumentos

> [!NOTE]
>  Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición de memoria muy baja, demasiada memoria usada por las variables de entorno o un error en el programa.
>
>  Puede intentar seguir estos pasos para corregir este error:
>
>  -   Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> -   Reducir el número y tamaño de los argumentos de línea de comandos a la aplicación.
> -   Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> -   Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> -   Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Había memoria suficiente para cargar el programa pero no hay suficiente memoria para crear el **argv** matriz. Esto puede deberse a condiciones muy poca memoria o inusualmente grande de las líneas de comandos o el uso de variables de entorno. Tenga en cuenta las siguientes soluciones:

- Aumente la cantidad de memoria disponible para el programa.

- Reducir el número y tamaño de los argumentos de línea de comandos.

- Reducir el tamaño del entorno quitando variables innecesarias.