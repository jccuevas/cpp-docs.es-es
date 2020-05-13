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
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825796"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE (Generar compilación instrumentada de generación de perfiles)

Especifican la generación de un archivo .pgd mediante el enlazador para admitir la optimización guiada por perfiles (PGO). **/GENPROFILE** y **/FASTGENPROFILE** usan parámetros predeterminados diferentes. Use **/GENPROFILE** para favorecer la precisión en la velocidad y el uso de memoria durante la generación de perfiles. Use **/FASTGENPROFILE** para favorecer el menor uso de memoria y la velocidad de precisión.

## <a name="syntax"></a>Sintaxis

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **Exact exacto**|**] |** **MEMMAX =**_#_|**MEMMIN =**_#_| [**rutaDeAcceso**|**nopath** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_nombreDeArchivo_}] \
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **Exact exacto**|**] |** **MEMMAX =**_#_|**MEMMIN =**_#_| [**rutaDeAcceso**|**nopath** ] | [**TRACKEH** |**NOTRACKEH** ] | **PGD =**_nombreDeArchivo_}]

### <a name="arguments"></a>Argumentos

Se puede especificar cualquiera de los argumentos siguientes en **/GENPROFILE** o **/FASTGENPROFILE**. Los argumentos que se enumeran aquí separados**|** por un carácter de barra vertical () son mutuamente excluyentes. Use un carácter de coma (**,**) para separar las opciones.

**COUNTER32** &#124; **COUNTER64**<br/>
Use **COUNTER32** para especificar el uso de contadores de sondeo de 32 bits y **COUNTER64** para especificar contadores de sondeo de 64 bits. Cuando se especifica **/GENPROFILE**, el valor predeterminado es **COUNTER64**. Cuando se especifica **/FASTGENPROFILE**, el valor predeterminado es **COUNTER32**.

**Exacto** &#124; **noexact**<br/>
Use **Exact** para especificar incrementos interbloqueados seguros para subprocesos para los sondeos. **Noexact** especifica las operaciones de incremento no protegido para los sondeos. El valor predeterminado es **noexact**.

**MEMMAX**=*Valor*de MEMMAX,*valor* de **MEMMIN**=<br/>
Use **MEMMAX** y **MEMMIN** para especificar los tamaños de reserva máximo y mínimo para los datos de entrenamiento en memoria. El valor es la cantidad de memoria que se reserva en bytes. De forma predeterminada, estos valores se determinan mediante una heurística interna.

**Ruta de acceso** &#124; **nopath** <br/>
Use **path** para especificar un conjunto independiente de contadores PGO para cada ruta de acceso única a una función. Use **nopath** para especificar solo un conjunto de contadores para cada función. Cuando se especifica **/GENPROFILE**, el valor predeterminado es **path** . Cuando se especifica **/FASTGENPROFILE**, el valor predeterminado es **nopath** .

**TRACKEH** &#124; **NOTRACKEH** <br/>
Especifican si se deben usar contadores adicionales para mantener un recuento preciso cuando se produzcan excepciones durante el entrenamiento. Use **TRACKEH** para especificar contadores adicionales para un recuento exacto. Use **NOTRACKEH** para especificar contadores únicos para el código que no usa el control de excepciones o que no encuentra excepciones en los escenarios de entrenamiento.  Cuando se especifica **/GENPROFILE**, el valor predeterminado es **TRACKEH** . Cuando se especifica **/FASTGENPROFILE**, el valor predeterminado es **NOTRACKEH** .

**PGD**=*Nombre de archivo* PGD<br/>
Especifica un nombre de archivo base para el archivo .pgd. De forma predeterminada, el enlazador usa el nombre de archivo de imagen ejecutable base con una extensión .pgd.

## <a name="remarks"></a>Observaciones

Las opciones **/GENPROFILE** y **/FASTGENPROFILE** indican al enlazador que genere el archivo de instrumentación de generación de perfiles necesario para admitir el entrenamiento de la aplicación para la optimización guiada por perfiles (PGO). Estas opciones son nuevas en Visual Studio 2015. Prefiera estas opciones para las opciones **/LTCG: PGINSTRUMENT**, **/PGD** y **/POGOSAFEMODE** desusadas y las variables de entorno **POGOSAFEMODE**, **VCPROFILE_ALLOC_SCALE** y **VCPROFILE_PATH** . La información de generación de perfiles creada mediante el entrenamiento de la aplicación se usa como entrada para realizar optimizaciones dirigidas de todo el programa durante las compilaciones. Se pueden establecer opciones adicionales para controlar diversas características de generación de perfiles de rendimiento durante el entrenamiento de la aplicación y las compilaciones. Las opciones predeterminadas especificadas por **/GENPROFILE** proporcionan resultados más precisos, especialmente para aplicaciones multiproceso grandes y complejas. La opción **/FASTGENPROFILE** usa valores predeterminados diferentes para un menor consumo de memoria y un rendimiento más rápido durante el entrenamiento, a costa de la precisión.

La información de generación de perfiles se captura cuando se ejecuta la aplicación instrumentada después de compilar mediante **/GENPROFILE** de **/FASTGENPROFILE**. Esta información se captura cuando se especifica la opción del vinculador [/USEPROFILE](useprofile.md) para realizar el paso de generación de perfiles y, a continuación, se usa para guiar el paso de compilación optimizado. Para obtener más información sobre cómo entrenar la aplicación y los detalles sobre los datos recopilados, consulte [optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

También debe especificar **/LTCG** al especificar **/GENPROFILE** o **/FASTGENPROFILE**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** del**vinculador** > de **propiedades** > de configuración.

1. Escriba las opciones y los argumentos de **/GENPROFILE** o **/FASTGENPROFILE** en el cuadro **opciones adicionales** . Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)<br/>
[/LTCG (Generación de código en tiempo de enlace)](ltcg-link-time-code-generation.md)<br/>
