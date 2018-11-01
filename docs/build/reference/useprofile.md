---
title: / USEPROFILE (datos de uso PGO con LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 4b780bed3b92b874f2bf18fb0235e8e2baf95ae9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550636"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (ejecutar PGO en modo de seguro para subprocesos)

Esta opción del vinculador junto con [/LTCG (generación de código en tiempo de vínculo](ltcg-link-time-code-generation.md) indica al vinculador que cree mediante el uso de datos de entrenamiento de optimización guiada por perfiles (PGO).

## <a name="syntax"></a>Sintaxis

> **/ USEPROFILE**[**:**{**agresivo al VOLANTE**|**PGD =**_filename_}]

### <a name="arguments"></a>Argumentos

**AGRESIVA**<br/>
Este argumento opcional especifica que se deben usar las optimizaciones de velocidad agresiva durante la generación de código optimizado.

**PGD**=*nombre de archivo*<br/>
Especifica un nombre de archivo base para el archivo .pgd. De forma predeterminada, el vinculador utiliza el nombre de archivo ejecutable base con una extensión de pgd.

## <a name="remarks"></a>Comentarios

El **/useprofile** se utiliza la opción del vinculador junto con **/LTCG** para generar o actualizar una versión optimizada según los datos de entrenamiento de PGO. Es el equivalente de desusado **/LTCG: PGUPDATE** y **/LTCG: PGOPTIMIZE** opciones.

El elemento opcional **agresivo al VOLANTE** argumento deshabilita relacionados con el tamaño de la heurística para intentar optimizar la velocidad. Esto puede dar lugar a que las optimizaciones que esencialmente aumentar el tamaño del archivo ejecutable y no se pueden aumentar la velocidad resultante. Debe generar perfiles y comparar los resultados de utilizar y no utilizarlo **agresivo al VOLANTE**. Este argumento debe especificarse explícitamente; no está habilitado de forma predeterminada.

El **PGD** argumento especifica un nombre opcional para el entrenamiento .pgd archivo de datos, igual que en [/GENPROFILE o/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Es el equivalente de desusado **/PGD** cambie. De forma predeterminada, o si no hay ningún *filename* se especifica, un archivo .pgd que tenga el mismo nombre base que se usa el archivo ejecutable.

El **/useprofile** opción del vinculador es nueva en Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. En el **generación de código de tiempo de vínculo** propiedad, elija **Use generación de código de tiempo de vínculo (/ LTCG)**.

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/useprofile** opción y los argumentos opcionales en la **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/GENPROFILE y /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)<br/>
[Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
