---
title: /LTCG (generación de código en tiempo de vínculo) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc4266e8b01201226c53584bed9f90ed9dcabef7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703738"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Generación de código en tiempo de enlace)

Use **/LTCG** para realizar la optimización de todo el programa, o crear la instrumentación de optimización guiada por perfiles (PGO), realizar el entrenamiento y crear guiada por perfiles con optimización para compilaciones.

## <a name="syntax"></a>Sintaxis

> **/ LTCG**[**:**{**INCREMENTAL**|**NOSTATUS**|**ESTADO** | **OFF**}]<br/>

Estas opciones están en desuso a partir de Visual Studio 2015:

> **/ LTCG:**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Argumentos

**INCREMENTAL** (opcional)<br/>
Especifica que el vinculador solo aplica todo el programa optimización o en tiempo de vínculo de generación de código (LTCG) al conjunto de archivos afectados por una modificación, en lugar de todo el proyecto. De forma predeterminada, esta marca no se establece cuando **/LTCG** se especifica, y todo el proyecto se vincula con la optimización de todo el programa.

**NOSTATUS** &#124; **estado** (opcional)<br/>
Especifica si el vinculador muestra un indicador de progreso que muestra qué porcentaje del vínculo está completado. De forma predeterminada, no se muestra esta información de estado.

**DESACTIVAR** (opcional)<br/>
Deshabilita la generación de código en tiempo de vínculo. Este comportamiento es el mismo que cuando **/LTCG** no se especifica en la línea de comandos.

**PGINSTRUMENT** (opcional)<br/>
Esta opción está en desuso a partir de Visual Studio 2015. En su lugar, use **/LTCG** y [/GENPROFILE o/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) para generar una compilación instrumentada para la optimización guiada por perfiles. Los datos que se recopilan de las ejecuciones instrumentadas se utilizan para crear una imagen optimizada. Para obtener más información, consulte [optimización guiada por perfiles](profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG: PGI**.

**PGOPTIMIZE** (opcional)<br/>
Esta opción está en desuso a partir de Visual Studio 2015. En su lugar, use **/LTCG** y [/useprofile](useprofile.md) para crear una imagen optimizada. Para obtener más información, consulte [optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG: PGO**.

**PGUPDATE** (opcional)<br/>
Esta opción está en desuso a partir de Visual Studio 2015. En su lugar, use **/LTCG** y **/useprofile** para volver a generar una imagen optimizada. Para obtener más información, consulte [optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG: pgu**.

## <a name="remarks"></a>Comentarios

El **/LTCG** opción indica al vinculador que llame al compilador y realice la optimización de todo el programa. También es posible realizar una optimización guiada por perfiles. Para obtener más información, consulte [optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md).

Con las siguientes excepciones, no se puede agregar las opciones del vinculador para la combinación de PGO de **/LTCG** y **/useprofile** que no se especificaron en la combinación de inicialización de PGO anterior de  **/ LTCG** y **/genprofile** opciones:

- [/BASE](../../build/reference/base-base-address.md)

- [/FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/ LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

Las opciones del vinculador que se especifican junto con el **/LTCG** y **/genprofile** opciones para inicializar PGO no tienen que especificarse cuando se crea mediante el uso de **/LTCG** y **/Useprofile**; ya que están implícitas.

El resto de este artículo se describe **/LTCG** en cuanto a la generación de código en tiempo de vínculo.

**/ LTCG** implícito con [/GL](../../build/reference/gl-whole-program-optimization.md).

El vinculador invoca la generación de código en tiempo de vínculo si se pasa un módulo que se compiló usando **/GL** o un módulo MSIL (vea [archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)). Si no especifica explícitamente **/LTCG** cuando se pasa **/GL** o módulos MSIL al vinculador, el vinculador finalmente lo detecta y se reinicia el vínculo mediante el uso de **/LTCG**. Especificar explícitamente **/LTCG** cuando se pasa **/GL** y rendimiento de la compilación de módulos MSIL al vinculador para el más rápido posible.

Para obtener un rendimiento más rápido, use **/LTCG: INCREMENTAL**. Esta opción indica al vinculador que solo debe volver a optimizar el conjunto de archivos a los que haya afectado un cambio de archivo de origen, en lugar de todo el proyecto. Esto puede reducir significativamente el tiempo de vínculo necesario. No es la misma opción como la vinculación incremental.

**/LTCG** no es válido con [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).

Cuando **/LTCG** se utiliza para vincular los módulos compilados con [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), o [/Ox](../../build/reference/ox-full-optimization.md), el se realizan las siguientes optimizaciones:

- Inserción entre módulos

- Asignación de registros entre procedimientos (solo los sistemas operativos de 64 bits)

- Convención de llamada personalizada (solo x86)

- Desplazamiento de TLS pequeño (solo x86)

- Alineamiento doble de pila (solo x86)

- Desambiguación de memoria mejorada (mejor información de interferencias para las variables globales y los parámetros de entrada)

> [!NOTE]
> El vinculador determina las optimizaciones que se usaron para compilar cada función y aplica las mismas optimizaciones en tiempo de vinculación.

Usar **/LTCG** y **/Ogt** hace optimización de doble alineación.

Si **/LTCG** y **/Ogs** se especifica, no se realiza la doble alineación. Si la mayoría de las funciones en una aplicación se compila para acelerar el proceso, con unas cuantas funciones compiladas para tamaño (por ejemplo, mediante la [optimizar](../../preprocessor/optimize.md) pragma), el compilador alinea doble las funciones que están optimizadas para el tamaño, si llama a funciones que requieren doble alineación.

Si el compilador puede identificar todos los sitios de llamada de una función, el compilador omite los modificadores de convención de llamada explícitos en una función e intenta optimizar la convención de llamada de la función:

- Se pasan parámetros en los registros

- Se reordenan parámetros para la alineación

- Se quitan parámetros sin utilizar

Si se llama a una función a través de un puntero a función, o si una función se llama desde fuera de un módulo que se compila con **/GL**, el compilador no intenta optimizar la convención de llamada de la función.

> [!NOTE]
> Si usa **/LTCG** y volver a definir `mainCRTStartup`, la aplicación puede tener un comportamiento imprevisible relacionada con el código de usuario que se ejecuta antes de que se inicializan los objetos globales. Hay tres formas de solucionar este problema: no redefinir `mainCRTStartup`, no compilar el archivo que contiene `mainCRTStartup` utilizando **/LTCG**, o inicializar las variables globales y los objetos estáticamente.

### <a name="ltcg-and-msil-modules"></a>Módulos /LTCG y MSIL

Los módulos que se compilan con [/GL](../../build/reference/gl-whole-program-optimization.md) y [/clr](../../build/reference/clr-common-language-runtime-compilation.md) pueden utilizarse como entradas del vinculador cuando se especifica **/LTCG** .

- **/ LTCG** puede aceptar archivos objeto nativos y archivos de objeto nativo y administrado mixto (compilado mediante **/CLR**). El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

- **/ LTCG: PGI** no acepta módulos nativos compilados mediante el uso de **/GL** y   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Vea [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **General** página de propiedades.

1. Modifique la propiedad **Optimización de todo el programa** .

También puede aplicar **/LTCG** a compilaciones concretas si elige **generar** > **optimización guiada por perfiles** en la barra de menús, o eligiendo uno del perfil Opciones de optimización guiadas en el menú contextual para el proyecto.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
