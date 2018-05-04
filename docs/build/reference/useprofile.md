---
title: / USEPROFILE (datos de uso PGO con LTCG) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156a571eaa3db31b8c5345f1550346503651665d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (PGO ejecutar en modo seguro para subprocesos)

Esta opción del vinculador junto con [/LTCG (generación de código en tiempo de vínculo](ltcg-link-time-code-generation.md) indica al vinculador para compilar utilizando los datos de entrenamiento de optimización guiada por perfiles (PGO).

## <a name="syntax"></a>Sintaxis

> **/ USEPROFILE**[**:**{**dinámico**|**PGD =**_filename_}]

### <a name="arguments"></a>Argumentos

**AGRESIVA**<br/>
Este argumento opcional especifica que se deben usar las optimizaciones de velocidad agresiva durante la generación de código optimizado.

**PGD**=*nombre de archivo*<br/>
Especifica un nombre de archivo base para el archivo .pgd. De forma predeterminada, el vinculador usa el nombre del archivo ejecutable base con una extensión de pgd.

## <a name="remarks"></a>Comentarios

El **/useprofile** opción del vinculador se utiliza junto con **/LTCG** para generar o actualizar una versión optimizada en función de los datos de entrenamiento de PGO. Es el equivalente de las regiones **/LTCG: PGUPDATE** y **/LTCG: PGOPTIMIZE** opciones.

Opcional **dinámico** argumento deshabilita relacionados con el tamaño de la heurística para intentar optimizar para máxima velocidad. Esto puede dar lugar a que las optimizaciones que esencialmente aumente el tamaño de su archivo ejecutable y no se pueden aumentar la velocidad resultante. Debe generar un perfil y comparar los resultados del uso y no usa **dinámico**. Este argumento debe especificarse explícitamente; no está habilitado de forma predeterminada.

El **PGD** argumento especifica un nombre opcional para el archivo de PGD de datos de entrenamiento que se utiliza el mismo que en [/GENPROFILE o/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). Es el equivalente de las regiones **/PGD** cambiar. De forma predeterminada, o si no hay ningún *filename* se especifica, un archivo .pgd que tenga el mismo nombre base que se utiliza el archivo ejecutable.

El **/useprofile** opción del vinculador es nueva en Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. En el **generación de código de tiempo de vínculo** propiedad, elija **generación de código de tiempo de vínculo de uso (/ LTCG)**.

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/useprofile** opción y los argumentos opcionales en la **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/GENPROFILE y /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/ LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)<br/>
[Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
