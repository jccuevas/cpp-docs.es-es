---
title: Error en tiempo de ejecución de C R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 60e6475a84d2662ad3718e04dba879dc06afeee7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214082"
---
# <a name="c-runtime-error-r6008"></a>Error en tiempo de ejecución de C R6008

No hay suficiente espacio para los argumentos

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo está provocada por una condición de memoria muy baja, demasiada memoria usada por las variables de entorno o un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Reducir el número y tamaño de los argumentos de línea de comandos a la aplicación.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Había memoria suficiente para cargar el programa pero no hay suficiente memoria para crear el **argv** matriz. Esto puede deberse a condiciones muy poca memoria o inusualmente grande de las líneas de comandos o el uso de variables de entorno. Tenga en cuenta las siguientes soluciones:

- Aumente la cantidad de memoria disponible para el programa.

- Reducir el número y tamaño de los argumentos de línea de comandos.

- Reducir el tamaño del entorno quitando variables innecesarias.