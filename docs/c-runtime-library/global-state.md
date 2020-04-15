---
title: Estado global en el CRT
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 487418da104b2edbc45b5d3a664e4385394ada31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377603"
---
# <a name="global-state-in-the-crt"></a>Estado global en el CRT

Algunas funciones del tiempo de ejecución de C universal (UCRT) utilizan el estado global. Por ejemplo, `setlocale()` establece la configuración regional para todo el programa, lo que afecta a los separadores de dígitos, la página de códigos de texto, etc.

El estado global del UCRT no se comparte entre las aplicaciones y el sistema operativo. Por ejemplo, si `setlocale()`la aplicación llama a , no afectará a la configuración regional de los componentes del sistema operativo que use el tiempo de ejecución de C o viceversa.

## <a name="os-specific-versions-of-crt-functions"></a>Versiones específicas del sistema operativo de las funciones CRT

En el UCRT, las funciones que interactúan con el `_o_`estado global tienen una función "twin", precedida con . Por ejemplo:

    `setlocale()` affects global state specific to the app.
    `_o_setlocale()` affects global state shared by all OS components, but not apps.

La única diferencia entre estas funciones "gemelos" es que cuando leen y escriben el estado `_o_`global de CRT, las versiones específicas del sistema operativo (es decir, las versiones que comienzan con ) usan la copia del sistema operativo del estado global en lugar de la copia del estado global de la aplicación.

Las versiones específicas del sistema `ucrt.osmode.lib`operativo de estas funciones se encuentran en . Por ejemplo, la versión `setlocale()` específica del sistema operativo de es`_o_setlocale()`

Hay dos maneras de aislar el estado CRT del componente del estado CRT de una aplicación:

- Vincule estáticamente el componente mediante las opciones del compilador /MT (liberación) o MTd (depuración). Para obtener más información, vea [/MD, /MT, /LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019). Tenga en cuenta que la vinculación estática puede aumentar considerablemente el tamaño binario.
- A partir de Windows 10 20H2, obtenga aislamiento de estado de CRT mediante la vinculación dinámica al CRT, pero llame a las exportaciones en modo de sistema operativo (las funciones que comienzan con _o_). Para llamar a las exportaciones en modo oS, vincule estáticamente como `/NODEFAULTLIB:libucrt.lib` antes, pero `/NODEFAULTLIB:libucrtd.lib` ignore el UCRT estático mediante la opción de vinculador (liberación) o (depuración) Consulte [/NODEFAULTLIB (Ignorar bibliotecas)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019) para obtener más información. Y `ucrt.osmode.lib` añadir a la entrada del vinculador.

> [!Note]
> En el código `setlocale()`fuente, escriba , no `_o_setlocale()`. Cuando se `ucrt.osmode.lib`vincula contra , el vinculador sustituirá automáticamente la versión específica del sistema operativo de la función. Es decir, `setlocale()` se sustituirá por `_o_setlocale()`.

La `ucrt.osmode.lib` vinculación con deshabilita algunas llamadas UCRT que solo están disponibles en modo de aplicación. Si intenta llamar a estos, se producirá un error de vínculo.

## <a name="global-state-affected-by-appos-separation"></a>Estado global afectado por la separación de aplicaciones/OS

El estado global afectado por la separación de la aplicación y el estado del sistema operativo incluye:

- [Datos de configuración regional](locale.md)
- Controladores de [señal](reference/signal.md) establecidos por señal
- Rutinas de terminación establecidas por [terminar](reference/set-terminate-crt.md)
- [errno y _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- Estado de generación de números aleatorios utilizado por [rand](reference/rand.md) y [srand](reference/srand.md)
- Funciones que devuelven un búfer que el usuario no necesita liberar: [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32 _gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror __wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- El búfer utilizado por [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) y [_set_new_mode](reference/set-new-mode.md)
- [fmode] (text-and-binary-mode-file-i-o.md)
- [Información de zona horaria](time-management.md)

## <a name="see-also"></a>Consulte también

[C Referencia de biblioteca en tiempo de ejecución](c-run-time-library-reference.md)