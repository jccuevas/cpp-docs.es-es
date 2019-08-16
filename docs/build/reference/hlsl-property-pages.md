---
title: Páginas de propiedades HLSL
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606400"
---
# <a name="hlsl-compiler-property-pages"></a>Páginas de propiedades del compilador HLSL

Las páginas de propiedades del compilador HLSL (fxc.exe) se pueden usar para configurar cómo se compilan los archivos individuales del sombreador HLSL. También puede especificar argumentos de línea de comandos para el compilador de HLSL mediante la propiedad **opciones adicionales** de la página de propiedades **línea de comandos** . Esto incluye argumentos que no se pueden configurar con otras propiedades de las páginas de propiedades de HLSL. Para obtener información sobre el compilador HLSL, vea [Effect-Compiler Tool](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409) (Herramienta Compilador de efectos)

## <a name="hlsl-general-property-page"></a>Página de propiedades general de HLSL

### <a name="additional-include-directories"></a>Directorios de inclusión adicionales

Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma. (/I [rutaDeAcceso])

### <a name="entrypoint-name"></a>Nombre de punto de entrada

Especifica el nombre del punto de entrada para el sombreador (/E [nombre]).

### <a name="disable-optimizations"></a>Deshabilitar optimizaciones

**Sí (/Od)** para deshabilitar las optimizaciones; de lo contrario, **No**. De forma predeterminada, el valor es **Sí (/Od)** para las configuraciones **Debug** y **No** para las configuraciones **Release**.

El argumento de la línea de comandos **/Od** para el compilador HLSL aplica implícitamente el argumento de la línea de comandos **/Gfp**, pero la salida no puede ser idéntico a la que se genera al pasar los dos argumentos de la línea de comandos **/Od** y **/Gfp** de forma explícita.

### <a name="enable-debugging-information"></a>Habilitar información de depuración

**Sí (/Zi)** para habilitar la información de depuración; en caso contrario, **No**. De forma predeterminada, el valor es **Sí (/Zi)** para las configuraciones **Debug** y **No** para las configuraciones **Release**.

### <a name="shader-type"></a>Tipo de sombreador

Especifica el tipo de sombreador. Cada tipo de sombreador implementa partes diferentes de la canalización de gráficos. Algunos tipos de sombreadores solo están disponibles en los modelos de sombreador más recientes (que se especifican mediante la propiedad **Modelo de sombreador**); por ejemplo, los sombreadores de cálculo se introdujeron en el modelo de sombreador 5.

Esta propiedad se corresponde con la parte **\[tipo]** del argumento de la línea de comandos **/T \[tipo]_\[modelo]** para el compilador HLSL. La propiedad **Modelos de sombreador** especifica la parte **[modelo]** del argumento.

**Posibilidad**

- **Efecto**
- **Sombreador de vértices**
- **Sombreador de píxeles**
- **Sombreador de geometría**
- **Sombreador de casco**
- **Sombreador de dominios**
- **Sombreador de cálculo**
- **Library**
- **Generar objeto de firma raíz**

### <a name="shader-model"></a>Modelo de sombreador

Especifica el modelo de sombreador. Cada modelo de sombreador tiene funciones distintas. Por lo general, los modelos de sombreador más recientes ofrecen funciones ampliadas pero requieren hardware gráfico más moderno para ejecutar el código del sombreador. Algunos tipos de sombreadores (que se especifican mediante la propiedad **Modelo de sombreador**) solo están disponibles en los modelos de sombreador más recientes; por ejemplo, los sombreadores de cálculo se introdujeron en el modelo de sombreador 5.

Esta propiedad se corresponde con la parte **\[modelo]** del argumento de la línea de comandos **/T \[tipo]_\[modelo]** para el compilador HLSL. La propiedad **Tipo de sombreador** especifica la parte **[tipo]** del argumento.

### <a name="all-resources-bound"></a>Todos los recursos enlazados

El compilador asumirá que todos los recursos a los que puede hacer referencia un sombreador están enlazados y están en buen estado para la duración de la ejecución del sombreador (/all_resources_bound). Disponible para Shader Model 5.1 y versiones superiores.

### <a name="enable-unbounded-descriptor-tables"></a>Habilitar tablas de descriptores sin enlazar

Informe al compilador de que un sombreador puede contener una declaración de una matriz de recursos con un intervalo sin enlazar (/enable_unbounded_descriptor_tables). Disponible para Shader Model 5.1 y versiones superiores.

### <a name="set-root-signature"></a>Establecer firma raíz

Adjunte la firma raíz al código de bytes del sombreador (/setrootsignature). Disponible para Shader Model 5.0 y versiones superiores.

### <a name="preprocessor-definitions"></a>Definiciones de preprocesador

Agrega una o varias definiciones de símbolo de preprocesador para aplicar al archivo de código fuente HLSL. Use punto y coma para separar las definiciones de símbolo.

Esta propiedad se corresponde con el argumento de la línea de comandos **/D \[definiciones]** para el compilador HLSL.

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Compilar un efecto de sombreador de píxeles personalizado de Direct2D

Compile un efecto personalizado de Direct2D que contenga sombreadores de píxeles. No lo use para un efecto personalizado de proceso o vértice.

### <a name="multi-processor-compilation"></a>Compilación de varios procesadores

Ejecutar varias instancias al mismo tiempo.

## <a name="advanced-property-page"></a>Página de propiedades avanzadas

### <a name="suppress-startup-banner"></a>Suprimir la pancarta de inicio

Suprime la presentación de la pancarta de inicio y los mensajes de información. /nologo

### <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser mejor usar /WX en todas las compilaciones. Resolver todas las advertencias es una forma de asegurar el menor número posible de defectos de código difíciles de encontrar.

## <a name="output-files-property-page"></a>Página de propiedades archivos de salida

### <a name="header-variable-name"></a>Nombre de la variable de encabezado

Especifica un nombre para el nombre de la variable en el archivo de encabezado (/VN [nombre])

### <a name="header-file-name"></a>Nombre del archivo de encabezado

Especifica un nombre para el archivo de encabezado que contiene código de objeto. (/FH [nombre])

### <a name="object-file-name"></a>Nombre de archivo objeto

Especifica un nombre para el archivo objeto. (/Fo [nombre])

### <a name="assembler-output"></a>Salida del ensamblador

Especifica el contenido del archivo de salida del lenguaje de ensamblado. (/FC,/FX)

**Posibilidad**

- **Sin lista** : no hay ninguna lista.
- **Lista de solo ensamblado** : archivo de código de ensamblado
- Código de **ensamblado y** código de ensamblado Hex y archivo de lista hexadecimal

### <a name="assembler-output-file"></a>Archivo de salida del ensamblador

Especifica el nombre de archivo del archivo de lista de código de ensamblado

## <a name="see-also"></a>Vea también

[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)<br>
[Páginas de propiedades Línea de comandos](command-line-property-pages.md)<br>
[Compiling Shaders](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409) (Sombreadores de compilación)
