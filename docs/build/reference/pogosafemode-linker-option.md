---
title: / POGOSAFEMODE (ejecutar PGO en modo de seguro para subprocesos)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: f210884d693ef0d778943580b9c5a7b2ec2ea336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544435"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (ejecutar PGO en modo de seguro para subprocesos)

**La opción/PogoSafeMode está en desuso a partir de Visual Studio 2015**. Use la [/genprofile: exacta](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) y **/GENPROFILE:NOEXACT** opciones en su lugar. El **/PogoSafeMode** opción del vinculador especifica que se crea la compilación instrumentada para utilizar el modo seguro para subprocesos para la captura de datos de perfil durante la optimización guiada por perfiles (PGO) las ejecuciones de entrenamiento.

## <a name="syntax"></a>Sintaxis

> **/POGOSAFEMODE**

## <a name="remarks"></a>Comentarios

Optimización guiada por perfiles (PGO) tiene dos posibles modos durante la fase de generación de perfiles: *modo rápido* y *modo seguro*. Al generar perfiles en modo rápido, utiliza una instrucción de incremento para aumentar los contadores de datos. La instrucción de incremento es más rápida, pero no es seguro para subprocesos. Al generar perfiles en modo seguro, utiliza la instrucción de incremento entrelazados para aumentar los contadores de datos. Esta instrucción tiene la misma funcionalidad como la instrucción de incremento y es segura para subprocesos, pero es más lento.

El **/PogoSafeMode** opción establece la compilación instrumentada para usar el modo seguro. Esta opción solo se pueden usar cuando el desuso [/LTCG: PGINSTRUMENT](ltcg-link-time-code-generation.md) se especifica durante la fase del enlazador de instrumentación de PGO.

De forma predeterminada, la generación de perfiles PGO funciona en modo rápido. **/ POGOSAFEMODE** es necesario sólo si desea usar el modo seguro.

Para ejecutar la generación de perfiles PGO en modo seguro, debe usar **/genprofile: exacta** (opción preferida), o bien usar la variable de entorno [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md) o el modificador del vinculador   **/PogoSafeMode**, según el sistema. Si va a realizar la generación de perfiles en un x64 equipo, debe usar el modificador del vinculador. Si va a realizar la generación de perfiles en un x86 equipo, puede usar el modificador del vinculador o defina la variable de entorno en cualquier valor antes de iniciar el proceso de instrumentación de PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. En el **generación de código de tiempo de vínculo** propiedad, elija **optimización guiada por perfiles - instrumento (/ LTCG: PGINSTRUMENT)**.

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/PogoSafeMode** opción en el **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/GENPROFILE y /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)<br/>
[Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
