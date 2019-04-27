---
title: Error en tiempo de ejecución de C R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: 28e541b61b6381cd283578a0ce1909e5b39a4a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151921"
---
# <a name="c-runtime-error-r6026"></a>Error en tiempo de ejecución de C R6026

No hay espacio suficiente para la inicialización de stdio

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay varias razones posibles para este error, pero normalmente está causado por una condición muy poca memoria. También puede deberse a un error en la aplicación, por daños en las bibliotecas de Visual C++ que utiliza o un controlador.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Si la aplicación funcionaba correctamente antes de una instalación reciente de otra aplicación o controlador, utilice la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para quitar el nueva aplicación o el controlador e inténtelo de nuevo la aplicación.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar todas las copias de Microsoft Visual C++ Redistributable.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce cuando no hay suficiente memoria libre disponible para inicializar la compatibilidad estándar de E/S en el tiempo de ejecución de C. Este error suele producirse al iniciar la aplicación. Compruebe que la aplicación y los controladores y los archivos DLL que carga no dañar el montón durante el inicio.