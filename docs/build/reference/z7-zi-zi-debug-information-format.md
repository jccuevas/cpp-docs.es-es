---
title: /Z7, /Zi, /ZI (Formato de la información de depuración)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: e809c7af7465cde98db11eac8628b76d04f7e8b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316293"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Formato de la información de depuración)

Especifica el tipo de información de depuración creado para el programa y si esta información se conserva en archivos objeto o en un archivo de programa (PDB) de la base de datos.

## <a name="syntax"></a>Sintaxis

> **/ Z**{**7**|**i**|**I**}

## <a name="remarks"></a>Comentarios

Cuando el código se compila y se compila en modo de depuración, el compilador genera los nombres de símbolos para las funciones y variables, información de tipos y ubicaciones de número de línea para su uso por el depurador. Esta información de depuración simbólica pueden incluir en los archivos objeto (.obj archivos) generados por el compilador o en un archivo PDB independiente (un archivo .pdb) para el archivo ejecutable.  Las opciones de formato de la información de depuración se describen en las secciones siguientes.

### <a name="none"></a>Ninguna

De forma predeterminada, si no se especifica ninguna opción de formato de información de depuración, el compilador no genera ninguna información de depuración, por lo que la compilación es más rápida.

### <a name="z7"></a>/Z7

El **/Z7** opción genera archivos de objeto que también contienen información de depuración simbólica completa para su uso con el depurador. Estos archivos de objeto y el ejecutable generado pueden ser considerablemente mayores que los archivos que no tienen ninguna información de depuración. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea. No se genera ningún archivo PDB.

Para los distribuidores de versiones de depuración de bibliotecas de terceros, hay una ventaja de no tener un archivo PDB. Sin embargo, los archivos de objeto para los encabezados precompilados son necesarios durante la fase de vinculación de la biblioteca y para la depuración. Si no hay tipo sólo información (y ningún código) en el archivo de objeto .pch, también debe usar el [/Yl (Insertar referencia PCH para biblioteca de depuración)](yl-inject-pch-reference-for-debug-library.md) opción, que está habilitada de forma predeterminada, cuando compile la biblioteca.

El desuso [/Gm (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) opción no está disponible cuando **/Z7** se especifica.

### <a name="zi"></a>/ZI

El **/Zi** opción genera un archivo PDB independiente que contiene todas la depuración información simbólica para su uso con el depurador. La información de depuración no está incluida en los archivos objeto o ejecutable, lo que hace que sean mucho más pequeño.

El uso de **/Zi** no afecta a las optimizaciones. Sin embargo, **/Zi** implica **/debug**; vea [/DEBUG (Generate Debug Info)](debug-generate-debug-info.md) para obtener más información.

Al especificar ambos **/Zi** y **/CLR**, el <xref:System.Diagnostics.DebuggableAttribute> atributo no se coloca en los metadatos del ensamblado. Si lo desea, debe especificarlo en el código fuente. Este atributo puede afectar al rendimiento de la aplicación en tiempo de ejecución. Para obtener más información acerca de cómo los **atributo Debuggable** atributo afecta al rendimiento y cómo puede modificar el impacto de rendimiento, vea [facilitar una imagen de depuración](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

El compilador asigna el archivo PDB *proyecto*PDB. Si compila un archivo fuera de un proyecto, el compilador crea un archivo PDB denominado VC*x*.pdb, donde *x* es una concatenación del número de versión principal y secundaria de la versión del compilador en uso. El compilador incrusta el nombre del archivo PDB y una firma con marca de tiempo identificación en cada archivo de objeto creado con esta opción, que señala al depurador a la ubicación de la información simbólica y número de línea. El nombre y firma en el archivo PDB deben coincidir con el archivo ejecutable para símbolos que se va a cargar en el depurador. El depurador WinDBG puede cargar los símbolos que no coincidentes utilizando el `.symopt+0x40` comando. Visual Studio no tiene una opción similar para cargar los símbolos que no coincidentes.

Si crea una biblioteca de objetos que se compilaron mediante **/Zi**, el archivo .pdb asociado debe estar disponible cuando la biblioteca se vincula a un programa. Por lo tanto, si distribuye la biblioteca, también debe distribuir el archivo PDB. Para crear una biblioteca que contiene información de depuración sin usar archivos PDB, debe seleccionar la **/Z7** opción. Si usa las opciones de encabezados precompilados, información de depuración para el encabezado precompilado y el resto del código fuente se coloca en el archivo PDB.

### <a name="zi"></a>/ZI

El **/Zi** es similar a la opción **/Zi**, pero produce un archivo PDB en un formato que admita la [editar y continuar](/visualstudio/debugger/edit-and-continue-visual-cpp) característica. Para utilizar editar y continuar las características de depuración, debe usar esta opción. La característica Editar y continuar es útil para la productividad del desarrollador, pero puede causar problemas de conformidad del compilador, el rendimiento y tamaño de código. Dado que la mayoría de las optimizaciones son incompatibles con Editar y continuar, el uso **/Zi** deshabilita cualquier `#pragma optimize` instrucciones en el código. El **/Zi** opción también es compatible con el uso de la [ &#95; &#95;línea&#95; &#95; la macro predefinida](../../preprocessor/predefined-macros.md); código compilado con **/Zi** no se puede usar **&#95; &#95;Línea&#95; &#95;** como un argumento de plantilla sin tipo, aunque **&#95; &#95;línea&#95; &#95;** se pueden usar en las expansiones de macro.

El **/Zi** opción obliga a ambos el [/Gy (habilitar vinculación en el nivel de función)](gy-enable-function-level-linking.md) y [/FC (completa ruta de acceso del archivo de código fuente en diagnósticos)](fc-full-path-of-source-code-file-in-diagnostics.md) opciones que se utilizarán en la compilación.

**/ Zi** no es compatible con [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> El **/Zi** opción sólo está disponible en los compiladores con destino procesadores x86 y x64; esta opción del compilador no está disponible en los compiladores con destino procesadores ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Abra el **propiedades de configuración** > **C o C++** > **General** página de propiedades.

1. Modificar el **formato de información de depuración** propiedad. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)

