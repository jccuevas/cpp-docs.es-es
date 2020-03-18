---
title: Control de errores (CRT)
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
ms.openlocfilehash: d38aaf76a4901b12290782957db90049d815d278
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443324"
---
# <a name="error-handling-crt"></a>Control de errores (CRT)

Utilice estas rutinas para controlar los errores de programa.

## <a name="error-handling-routines"></a>Rutinas de control de errores

|Rutina|Uso|
|-------------|---------|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) (Macro)|Comprueba los errores lógicos de programación. Disponible en las versiones de lanzamiento y depuración de la biblioteca en tiempo de ejecución.|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) (Macros)|Similar a **assert**, pero disponible únicamente en las versiones de depuración de la biblioteca en tiempo de ejecución.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Indicador de error de restablecimiento. La llamada a **rewind** o el cierre de una secuencia también restablece el indicador de error.|
|[_eof](../c-runtime-library/reference/eof.md)|Comprueba el final de archivo en E/S de bajo nivel.|
|[feof](../c-runtime-library/reference/feof.md)|Prueba el fin del archivo. El final del archivo también se indica cuando **_read** devuelve 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Comprueba los errores de E/S de secuencia.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) (Macros)|Genera un informe similar a **printf**, pero disponible únicamente en las versiones de depuración de la biblioteca en tiempo de ejecución.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Modifica **__error_mode** para determinar una ubicación no predeterminada en donde el tiempo de ejecución de C escribe un mensaje de error si hay un error que podría finalizar el programa.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Establece el controlador de una llamada de función virtual pura.|

## <a name="see-also"></a>Consulte también

- [Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)
