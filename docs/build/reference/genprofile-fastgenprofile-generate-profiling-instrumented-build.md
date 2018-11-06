---
title: /GENPROFILE, /FASTGENPROFILE (Generar compilación instrumentada de generación de perfiles)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: e703c94d4a8b7cf7c70e68071959b775987f1710
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496452"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE (Generar compilación instrumentada de generación de perfiles)

Especifican la generación de un archivo .pgd mediante el enlazador para admitir la optimización guiada por perfiles (PGO). **/ GENPROFILE** y **/fastgenprofile** usan parámetros predeterminados diferentes. Use **/genprofile** para favorecer la precisión a través del uso de memoria y velocidad durante la generación de perfiles. Use **/fastgenprofile** se va a favorecer el menor uso de memoria y velocidad sobre la precisión.

## <a name="syntax"></a>Sintaxis

> **/ GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **EXACT**|**NOEXACT**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [ **Ruta**|**NOPATH** ] | [ **TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **EXACT**|**NOEXACT**] | **MEMMAX =**_#_|**MEMMIN =**_#_| [ **Ruta**|**NOPATH** ] | [ **TRACKEH** |**NOTRACKEH** ] | **PGD =**_filename_}]

### <a name="arguments"></a>Argumentos

Se puede especificar cualquiera de los siguientes argumentos a **/genprofile** o **/fastgenprofile**. Argumentos enumerados aquí separan por una barra vertical (**|**) caracteres son mutuamente excluyentes. Use una coma (**,**) carácter para separar las opciones.

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
Usar **COUNTER32** para especificar el uso de contadores de sondeo de 32 bits, y **COUNTER64** para especificar contadores de sondeo de 64 bits. Al especificar **/genprofile**, el valor predeterminado es **COUNTER64**. Al especificar **/fastgenprofile**, el valor predeterminado es **COUNTER32**.

**EXACTO** &AMP;#124; **NOEXACT**<br/>
Use **EXACT** para especificar incrementos interbloqueados de subprocesos para los sondeos. **NOEXACT** especifica las operaciones de incremento no protegido para los sondeos. El valor predeterminado es **NOEXACT**.

**MEMMAX**=*valor*, **MEMMIN**=*valor*<br/>
Use **MEMMAX** y **MEMMIN** para especificar los tamaños de reserva máximo y mínimo para datos de entrenamiento en memoria. El valor es la cantidad de memoria que se reserva en bytes. De forma predeterminada, estos valores se determinan mediante una heurística interna.

**RUTA DE ACCESO** &AMP;#124; **NOPATH**  <br/>
Use **ruta de acceso** para especificar un conjunto independiente de contadores PGO para cada ruta de acceso única a una función. Use **NOPATH** para especificar solo un conjunto de contadores para cada función. Al especificar **/genprofile**, el valor predeterminado es **ruta de acceso** . Al especificar **/fastgenprofile**, el valor predeterminado es **NOPATH** .

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
Especifican si se deben usar contadores adicionales para mantener un recuento preciso cuando se produzcan excepciones durante el entrenamiento. Use **TRACKEH** para especificar contadores adicionales para un recuento exacto. Usar **NOTRACKEH** para especificar contadores únicos para el código que no utiliza excepción control o que no produce excepciones en los escenarios de entrenamiento.  Al especificar **/genprofile**, el valor predeterminado es **TRACKEH** . Al especificar **/fastgenprofile**, el valor predeterminado es **NOTRACKEH** .

**PGD**=*nombre de archivo*<br/>
Especifica un nombre de archivo base para el archivo .pgd. De forma predeterminada, el enlazador usa el nombre de archivo de imagen ejecutable base con una extensión .pgd.

## <a name="remarks"></a>Comentarios

El **/genprofile** y **/fastgenprofile** opciones indican al vinculador para generar el archivo de instrumentación de generación de perfiles necesario para admitir el entrenamiento de la aplicación para la optimización guiada por perfiles (PGO). Estas opciones son nuevas en Visual Studio 2015. Prefiere estas opciones para el desuso **/LTCG: PGINSTRUMENT**, **/PGD** y **/PogoSafeMode** opciones y la **PogoSafeMode**,  **VCPROFILE_ALLOC_SCALE** y **VCPROFILE_PATH** variables de entorno. La información de generación de perfiles creada mediante el entrenamiento de la aplicación se usa como entrada para realizar optimizaciones dirigidas de todo el programa durante las compilaciones. Se pueden establecer opciones adicionales para controlar diversas características de generación de perfiles de rendimiento durante el entrenamiento de la aplicación y las compilaciones. Las opciones predeterminadas especificadas por **/genprofile** proporcionan resultados más precisos, especialmente para las aplicaciones multiproceso grandes y complejas. El **/fastgenprofile** opción utiliza valores predeterminados diferentes para un menor consumo de memoria y un rendimiento más rápido durante el entrenamiento, a costa de precisión.

Información de generación de perfiles se captura cuando se ejecuta la aplicación instrumentada después de compilar mediante el uso de **/genprofile** de **/fastgenprofile**. Esta información se captura cuando se especifica la [/useprofile](useprofile.md) paso de la opción del vinculador para realizar la generación de perfiles y, a continuación, se utiliza para guiar el paso de compilación optimizada. Para obtener más información sobre cómo entrenar su aplicación y obtener más información sobre los datos recopilados, vea [optimización guiada por perfiles](profile-guided-optimizations.md).

También debe especificar **/LTCG** al especificar **/genprofile** o **/fastgenprofile**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/genprofile** o **/fastgenprofile** opciones y argumentos en el **opciones adicionales** cuadro. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[/LTCG (Generación de código en tiempo de enlace)](../../build/reference/ltcg-link-time-code-generation.md)<br/>
