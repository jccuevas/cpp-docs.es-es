---
title: Error en tiempo de ejecución de C R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 22bf4b7e8951215d1a013edb29af1ebff7517ffc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197345"
---
# <a name="c-runtime-error-r6016"></a>Error en tiempo de ejecución de C R6016

espacio insuficiente para datos de subproceso

> [!NOTE]
> Si encuentra este mensaje de error mientras se ejecuta una aplicación, la aplicación se cerró porque tiene un problema de memoria interna. Hay muchas razones posibles para este error, pero a menudo se debe a una condición de memoria extremadamente baja, a un error de la aplicación o a un error en un complemento o extensión que usa la aplicación.
>
> Puede intentar seguir estos pasos para corregir este error:
>
> - Cierre otras aplicaciones en ejecución o reinicie el equipo para liberar memoria.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para reparar o reinstalar la aplicación.
> - Use la página **aplicaciones y características** o **programas y características** del **Panel de control** para quitar, reparar o reinstalar los complementos o extensiones usados por la aplicación.
> - Compruebe **Windows Update** en el **Panel de control** para las actualizaciones de software.
> - Busque una versión actualizada de la aplicación. Si el problema persiste, póngase en contacto con el proveedor de la aplicación.

**Información para programadores**

Este error se produce porque el programa no recibió memoria suficiente del sistema operativo para completar una llamada [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) o `_beginthreadex`, o bien `_beginthread` o `_beginthreadex`no ha inicializado el almacenamiento local del subproceso.

Cuando se inicia un subproceso nuevo, la biblioteca debe crear una base de datos interna para el subproceso. Si la base de datos no se puede ampliar utilizando la memoria proporcionada por el sistema operativo, el subproceso no se puede iniciar y se detiene el proceso de llamada. Esto puede ocurrir cuando el proceso ha creado demasiados subproceso o si se ha agotado el almacenamiento local para el subproceso.

Se recomienda que un archivo ejecutable que llame a la biblioteca en tiempo de ejecución de C (CRT) Use `_beginthreadex` para la creación de subprocesos en lugar de la API de Windows `CreateThread`. `_beginthreadex` inicializa el almacenamiento estático interno que usan muchas funciones CRT en el almacenamiento local de subprocesos. Si utiliza `CreateThread` para crear un subproceso, CRT puede finalizar el proceso con R6016 cuando se realiza una llamada a una función CRT que requiere que el almacenamiento estático interno se haya inicializado.
