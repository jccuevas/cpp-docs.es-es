---
title: Opciones de vínculo
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: ea71faab639a8c0a09d6e332618dd7e09159a4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351099"
---
# <a name="link-options"></a>Opciones de vínculo

El directorio lib de CRT incluye una serie de archivos de objetos pequeños que habilitan características de CRT específicas sin realizar ningún cambio en el código. Se denominan "opciones de vínculo" puesto que solo hay que agregarlas a la línea de comandos del enlazador para usarlas.

Las versiones en modo puro de CLR de estos objetos están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017. Use las versiones normales para código nativo y /clr.

|Nativo y /clr|Modo puro|Descripción|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Establece el modo de traducción de archivo predeterminado en binario. Consulte [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|N/D|Ofrece compatibilidad con comprobación de pila y alloca cuando no se use CRT.|
|commode.obj|pcommode.obj|Establece la marca global de confirmación en "commit". Consulte [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) y [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|N/D|Inicializa el apartamento MTA durante el inicio de EXE, lo que permite el uso de objetos COM en punteros inteligentes globales. No use esta opción para DLL, puesto que provoca la fuga de una referencia al apartamento MTA durante el apagado. Un vínculo a esta opción equivale a incluir combase.h y definir _EXE_INITIALIZE_MTA. |
|fp10.obj|N/D|Cambia el control de precisión predeterminado a 64 bits. Consulte [Compatibilidad con el punto flotante](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Establece un controlador de parámetros no válidos predeterminado que no hace nada, lo que significa que los parámetros no válidos que se pasen a funciones de CRT solo establecerán errno y devolverán un resultado de error.|
|legacy_stdio_float_rounding.obj|N/D|Se ha corregido la impresión de valores de punto flotante (por ejemplo, cuando se usa [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)) con Windows 10 19041 Universal C Runtime. Ahora redondea correctamente los números de punto flotante exactamente representables, y respeta el redondeo de punto flotante solicitado por [fesetenv](../c-runtime-library/reference/fesetenv1.md). Esta actualización de comportamiento está disponible en Visual Studio 2019 versión 16.2 y versiones posteriores. El comportamiento heredado se usa en versiones anteriores de Visual Studio o proporcionando esta opción de vínculo.|
|loosefpmath.obj|N/D|Se asegura de que el código de punto flotante tolera valores desnormalizados.|
|newmode.obj|pnewmode.obj|Hace que [malloc](../c-runtime-library/reference/malloc.md) llame al nuevo controlador en caso de error. Consulte [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md) y [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Deshabilita todo el procesamiento de argc y argv.|
|nochkclr.obj|N/D|No hace nada. Quitar del proyecto.|
|noenv.obj|pnoenv.obj|Deshabilita la creación de un entorno almacenado en caché para el CRT.|
|nothrownew.obj|pnothrownew.obj|Habilita la versión que no produce excepciones de new en el CRT. Consulte [Operadores new y delete](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Habilita la expansión de caracteres comodín de argumento de línea de comandos. Consulte [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Habilita de forma predeterminada la configuración regional por subproceso para todos los nuevos subprocesos.|
|wsetargv.obj|pwsetargv.obj|Habilita la expansión de caracteres comodín de argumento de línea de comandos. Consulte [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Consulte también

- [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
