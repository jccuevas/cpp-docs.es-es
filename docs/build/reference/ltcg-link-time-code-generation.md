---
title: /LTCG (Generación de código en tiempo de enlace)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 1e33d62694fe782b1a1719fa3c5a36c6fb04670a
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400626"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Generación de código en tiempo de enlace)

Use **/LTCG** para realizar la optimización de todo el programa o para crear la instrumentación de optimización guiada por perfiles (PGO), realizar cursos y crear versiones optimizadas guiadas por perfiles.

## <a name="syntax"></a>Sintaxis

> **/LTCG**[ **:** {**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]

Estas opciones estarán en desuso en Visual Studio 2015:

> **/LTCG:** {**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}

### <a name="arguments"></a>Argumentos

**INCREMENTAL**<br/>
(Opcional) Especifica que el enlazador solo aplica toda la optimización de programa o la generación de código en tiempo de vínculo (LTCG) al conjunto de archivos a los que afecta una modificación, en lugar de a todo el proyecto. De forma predeterminada, esta marca no se establece cuando se especifica **/LTCG** y todo el proyecto está vinculado al usar la optimización de todo el programa.

**NOSTATUS** &#124; **STATUS**<br/>
(Opcional) Especifica si el enlazador debe mostrar un indicador de progreso que indique qué porcentaje del vínculo está completado. De forma predeterminada, no se muestra esta información de estado.

**OFF**<br/>
(Opcional) Deshabilita la generación de código en tiempo de vínculo. Este comportamiento es el mismo que cuando no se especifica **/LTCG** en la línea de comandos.

**PGINSTRUMENT**<br/>
(Opcional) Esta opción está en desuso a partir de Visual Studio 2015. Es preferible usar **/LTCG** y [/GENPROFILE o /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) para generar una compilación instrumentada para la optimización guiada por perfiles. Los datos que se recopilan de las ejecuciones instrumentadas se usan para compilar una imagen optimizada. Para más información, vea [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG:PGI**.

**PGOPTIMIZE**<br/>
(Opcional) Esta opción está en desuso a partir de Visual Studio 2015. Es preferible usar **/LTCG** y [/USEPROFILE](useprofile.md) para compilar una imagen optimizada. Para más información, vea [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG:PGO**.

**PGUPDATE**<br/>
(Opcional) Esta opción está en desuso a partir de Visual Studio 2015. Es preferible usar **/LTCG** y **/USEPROFILE** para volver a compilar una imagen optimizada. Para más información, vea [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md). La forma abreviada de esta opción es **/LTCG:PGU**.

## <a name="remarks"></a>Comentarios

La opción **/LTCG** indica al enlazador que debe llamar al compilador y realizar la optimización de todo el programa. También es posible realizar una optimización guiada por perfiles. Para más información, vea [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

Salvo en las siguientes excepciones, no es posible agregar opciones del enlazador a la combinación PGO de **/LTCG** y **/USEPROFILE** que no se especificaron en la combinación de inicialización PGO anterior de las opciones **/LTCG** y **/GENPROFILE**:

- [/BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

Las opciones del enlazador que se especifiquen junto con las opciones **/LTCG** y **/GENPROFILE** para inicializar la PGO no tienen que especificarse al compilar con **/LTCG** y **/USEPROFILE**, ya que están implícitas.

En el resto de este artículo se explica **/LTCG** con respecto a la generación de código en tiempo de vinculación.

**/LTCG** está implícito con [/GL](gl-whole-program-optimization.md).

El enlazador invoca la generación de código en tiempo de vínculo si se pasa un módulo que se ha compilado con **/GL** o un módulo MSIL (vea [Archivos .netmodule como entrada del enlazador](netmodule-files-as-linker-input.md)). Si no se especifica explícitamente **/LTCG** al pasar **/GL** o módulos MSIL al enlazador, el enlazador finalmente lo detecta y se reinicia el vínculo mediante el uso de **/LTCG**. Especifique explícitamente **/LTCG** al pasar **/GL** y módulos MSIL al enlazador para conseguir el rendimiento de compilación más rápido posible.

Para obtener un rendimiento más rápido, use **/LTCG:INCREMENTAL**. Esta opción indica al enlazador que solo debe volver a optimizar el conjunto de archivos a los que haya afectado un cambio de archivo de origen, en lugar de todo el proyecto. Esto puede reducir considerablemente el tiempo de vínculo necesario y no se considera la misma opción que la vinculación incremental.

**/LTCG** no es válido con [/INCREMENTAL](incremental-link-incrementally.md).

Cuando se usa **/LTCG** para vincular los módulos compilados mediante [/Og](og-global-optimizations.md), [/O1](o1-o2-minimize-size-maximize-speed.md), [/O2](o1-o2-minimize-size-maximize-speed.md) u [/Ox](ox-full-optimization.md), se realizan estas optimizaciones:

- Inserción entre módulos

- Asignación de registros entre procedimientos (solo los sistemas operativos de 64 bits)

- Convención de llamada personalizada (solo x86)

- Desplazamiento de TLS pequeño (solo x86)

- Alineamiento doble de pila (solo x86)

- Desambiguación de memoria mejorada (mejor información de interferencias para las variables globales y los parámetros de entrada)

> [!NOTE]
> El vinculador determina las optimizaciones que se usaron para compilar cada función y aplica las mismas optimizaciones en tiempo de vinculación.

El uso de **/LTCG** y **/Ogt** provoca una optimización de doble alineación.

Si se especifican **/LTCG** y **/Ogs**, no se realizará la doble alineación. Si la mayoría de las funciones de una aplicación se compila para conseguir velocidad, aunque algunas funciones se compilen por motivos de tamaño (por ejemplo, mediante el pragma [optimize](../../preprocessor/optimize.md)), el compilador alineará de forma doble las funciones que están optimizadas para el tamaño si llaman a funciones que necesitan una doble alineación.

Si el compilador puede identificar todos los sitios de llamada de una función, el compilador omite los modificadores de convención de llamada explícitos en una función e intenta optimizar la convención de llamada de la función:

- Se pasan parámetros en los registros

- Se reordenan parámetros para la alineación

- Se quitan parámetros sin utilizar

Si se llama a una función a través de un puntero de función, o si una función se llama desde fuera de un módulo que se compila con **/GL**, el compilador no intenta optimizar la convención de llamada de la función.

> [!NOTE]
> Si usa **/LTCG** y vuelve a definir `mainCRTStartup`, la aplicación puede tener un comportamiento impredecible que relaciona el código de usuario que se ejecuta antes de que se inicialicen los objetos globales. Hay tres formas de solucionar este problema: no redefinir `mainCRTStartup`, no compilar el archivo que contiene `mainCRTStartup` mediante **/LTCG** o inicializar las variables globales y los objetos estáticamente.

### <a name="ltcg-and-msil-modules"></a>Módulos /LTCG y MSIL

Los módulos que se compilan con [/GL](gl-whole-program-optimization.md) y [/clr](clr-common-language-runtime-compilation.md) pueden utilizarse como entradas del vinculador cuando se especifica **/LTCG** .

- **/LTCG** puede aceptar archivos objeto nativos y archivos objeto mixtos nativos/administrados (compilados mediante **/clr**). Las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores.

- **/LTCG:PGI** no acepta módulos nativos compilados mediante **/GL** y **/clr**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **General**.

1. Modifique la propiedad **Optimización de todo el programa** .

También puede aplicar **/LTCG** a compilaciones concretas si elige **Compilar** > **Optimización guiada** por perfiles en la barra de menús, o si selecciona una de las opciones de Optimización guiada por perfiles del menú contextual del proyecto.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
