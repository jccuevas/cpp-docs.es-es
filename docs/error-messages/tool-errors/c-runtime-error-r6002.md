---
title: Error en tiempo de ejecución de C R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: f8b5fe69c9fd688f4d0a181176cda247cde9ac11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380544"
---
# <a name="c-runtime-error-r6002"></a>Error en tiempo de ejecución de C R6002

compatibilidad de punto flotante no cargado

No se vinculó la biblioteca de punto flotante es necesaria.

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo está provocada por los defectos de código de la aplicación o al intentar ejecutar una aplicación que no se generó para el procesador del equipo en particular.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error puede producirse en la aplicación cuando no se vinculó la biblioteca de punto flotante. Busque una de estas causas:

- Una cadena de formato para un `printf_s` o `scanf_s` función contiene una especificación de formato de punto flotante y el programa no contiene los valores de punto flotante o variables. Para corregir este problema, utilice un argumento de punto flotante para que coincida con la especificación de formato de punto flotante o realizar una asignación de punto flotante en otro lugar en el programa. Esto hace que la compatibilidad de punto flotante que se va a cargar.

- El compilador minimiza el tamaño de un programa mediante la carga de la compatibilidad de punto flotante solo cuando sea necesario. El compilador no puede detectar las operaciones de punto flotante o las especificaciones de formato de punto flotante en cadenas de formato, por lo que no se carga las rutinas de punto flotante es necesarias. Para corregir este problema, utilice una especificación de formato de punto flotante y proporciona un argumento de punto flotante o realizar una asignación de punto flotante en otro lugar en el programa. Esto hace que la compatibilidad de punto flotante que se va a cargar.

- En un programa con varios lenguajes, se especificó una biblioteca C antes de una biblioteca de FORTRAN cuando se vinculó el programa. Volver a vincular y especifique la biblioteca de C por última vez.