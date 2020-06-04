---
title: Error en tiempo de ejecución de C R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 214b6548cc7a3b880223503c2f3e9222d64212ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197398"
---
# <a name="c-runtime-error-r6008"></a>Error en tiempo de ejecución de C R6008

no hay espacio suficiente para los argumentos

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero a menudo se debe a una condición de memoria extremadamente baja, demasiada memoria para las variables de entorno o un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Reduzca el número y el tamaño de los argumentos de la línea de comandos a la aplicación.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Memoria suficiente para cargar el programa, pero no hay suficiente memoria para crear la matriz **argv** . Esto puede deberse a condiciones de memoria extremadamente bajas o a líneas de comandos o uso de variables de entorno inusualmente grandes. Considere una de las siguientes soluciones:

- Aumente la cantidad de memoria disponible para el programa.

- Reduzca el número y el tamaño de los argumentos de la línea de comandos.

- Reduzca el tamaño del entorno quitando las variables innecesarias.
