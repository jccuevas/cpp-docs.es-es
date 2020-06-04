---
title: Error en tiempo de ejecución de C R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 64391f8ec05a99bb85a9d6cd00d6488a945fdb62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197358"
---
# <a name="c-runtime-error-r6009"></a>Error en tiempo de ejecución de C R6009

no hay espacio suficiente para el entorno

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo se debe a una condición de memoria extremadamente baja, demasiada memoria para las variables de entorno o un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Memoria suficiente para cargar el programa, pero no hay suficiente memoria para crear la matriz **envp** .  Esto puede deberse a condiciones de memoria extremadamente bajas o a un uso de variables de entorno inusualmente grande. Considere una de las siguientes soluciones:

- Aumente la cantidad de memoria disponible para el programa.

- Reduzca el número y el tamaño de los argumentos de la línea de comandos.

- Reduzca el tamaño del entorno quitando las variables innecesarias.
