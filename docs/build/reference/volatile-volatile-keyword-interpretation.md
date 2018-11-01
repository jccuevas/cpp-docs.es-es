---
title: /volatile (interpretación de la palabra clave volatile)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: da2d981d9fcca6be66a7fd495e7c76670ed8e3ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502523"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretación de la palabra clave volatile)

Especifica cómo el [volátil](../../cpp/volatile-cpp.md) palabra clave es que interpretarse.

## <a name="syntax"></a>Sintaxis

> **/ volatile:**{**iso**|**ms**}

## <a name="arguments"></a>Argumentos

**/ volatile: ISO**<br/>
Selecciona strict `volatile` semántica como se define en el lenguaje estándar ISO C++. Adquisición y liberación de semántica no se garantiza en accesos volátiles. Si el compilador tiene como destino ARM, se trata de la interpretación predeterminada de `volatile`.

**/ volatile: MS**<br/>
Selecciona extendidas de Microsoft `volatile` semántica, que agrega garantías más allá del lenguaje C++ estándar de ISO de ordenación de memoria. Adquisición o liberación de semántica se garantiza en accesos volátiles. Sin embargo, esta opción también hace que el compilador genere barreras de memoria de hardware, lo que podrían producir una sobrecarga significativa en ARM y otras arquitecturas de ordenación de memoria débiles. Si el compilador tiene como destino cualquier plataforma excepto la ARM, ésta es la interpretación predeterminada de `volatile`.

## <a name="remarks"></a>Comentarios

Se recomienda encarecidamente que utilice **/volatile: ISO** junto con primitivos explícitos de sincronización y funciones intrínsecas del compilador al tratar con memoria compartida entre subprocesos. Para obtener más información, consulte [volátil](../../cpp/volatile-cpp.md).

Si el código existente o cambiar esta opción en medio de un proyecto, puede ser útil habilitar la advertencia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) para identificar las ubicaciones de código que se ven afectadas por la diferencia semántica.

No hay ningún `#pragma` equivalente para controlar esta opción.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Para establecer el /volatile opción del compilador en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue **/volatile: ISO** o **/volatile: MS** y, a continuación, elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[volatile](../../cpp/volatile-cpp.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
