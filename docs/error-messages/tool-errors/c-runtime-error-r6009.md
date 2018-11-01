---
title: C Runtime Error R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 5e1914d5d2f665609cfc24c2db3dc8a123d7e83f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591313"
---
# <a name="c-runtime-error-r6009"></a>C Runtime Error R6009

No hay suficiente espacio para el entorno

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición de memoria muy baja, demasiada memoria usada por las variables de entorno o un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Había memoria suficiente para cargar el programa, pero no hay suficiente memoria para crear el **envp** matriz.  La causa puede ser extremadamente bajos de memoria, o bien el uso de variables de entorno inusualmente grande. Tenga en cuenta las siguientes soluciones:

- Aumente la cantidad de memoria disponible para el programa.

- Reducir el número y tamaño de los argumentos de línea de comandos.

- Reducir el tamaño del entorno quitando variables innecesarias.