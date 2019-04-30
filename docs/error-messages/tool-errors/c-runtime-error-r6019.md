---
title: Error en tiempo de ejecución de C R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: 93d340b2a12a00420a9003429251387b2f04ad37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214110"
---
# <a name="c-runtime-error-r6019"></a>Error en tiempo de ejecución de C R6019

no se puede abrir el dispositivo de consola

> [!NOTE]
> Si encuentra este mensaje de error al ejecutar una aplicación, la aplicación se cerró porque ha intentado acceder a la consola, pero no tiene permisos suficientes. Hay varias razones posibles para este error, pero suele ser porque se debe ejecutar el programa como administrador, o hay un error en el programa.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Ejecute el programa como administrador.
> - Use la **aplicaciones y características** o **programas y características** página en el **Panel de Control** para reparar o reinstalar el programa.
> - Comprobar **Windows Update** en el **Panel de Control** las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque la aplicación llama a una función de la consola, pero el sistema operativo no le ha concedido acceso a la consola. Excepto en el modo de depuración, consola generalmente no se permiten funciones en las aplicaciones de Microsoft Store. Si la aplicación requiere privilegios de administrador para su ejecución, asegúrese de que está instalado para ejecutarse como administrador de forma predeterminada.