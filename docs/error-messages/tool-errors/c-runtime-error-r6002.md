---
title: Error en tiempo de ejecución de C R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: b2e617b6f7841f1aa7e6fd2f6962c0e117fab6c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197423"
---
# <a name="c-runtime-error-r6002"></a>Error en tiempo de ejecución de C R6002

compatibilidad de punto flotante no cargada

La biblioteca de punto flotante necesaria no estaba vinculada.

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema interno. Hay varias razones posibles para este error, pero a menudo se debe a un defecto en el código de la aplicación o a un intento de ejecutar una aplicación que no se compiló para el procesador del equipo en particular.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar el programa.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error puede producirse en la aplicación cuando la biblioteca de punto flotante no estaba vinculada. Compruebe una de estas causas:

- Una cadena de formato para una función `printf_s` o `scanf_s` contenía una especificación de formato de punto flotante y el programa no contenía ningún valor o variable de punto flotante. Para corregir este problema, use un argumento de punto flotante para que se corresponda con la especificación de formato de punto flotante o realice una asignación de punto flotante en otra parte del programa. Esto hace que se cargue la compatibilidad de punto flotante.

- El compilador minimiza el tamaño de un programa mediante la carga de la compatibilidad de punto flotante solo cuando es necesario. El compilador no puede detectar las operaciones de punto flotante o las especificaciones de formato de punto flotante en las cadenas de formato, por lo que no carga las rutinas de punto flotante necesarias. Para corregir este problema, use una especificación de formato de punto flotante y proporcione un argumento de punto flotante, o realice una asignación de punto flotante en otra parte del programa. Esto hace que se cargue la compatibilidad de punto flotante.

- En un programa de lenguaje mixto, se especificó una biblioteca de C antes de una biblioteca de FORTRAN cuando se vinculó el programa. Volver a vincular y especificar la biblioteca de C en último lugar.
