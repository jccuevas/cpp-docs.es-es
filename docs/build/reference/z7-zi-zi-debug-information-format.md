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
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078262"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Formato de la información de depuración)

Especifica el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto o en un archivo de base de datos de programa (PDB).

## <a name="syntax"></a>Sintaxis

> **/Z**{**7**|**i**|**i**}

## <a name="remarks"></a>Observaciones

Cuando el código se compila y se compila en modo de depuración, el compilador genera nombres de símbolos para las funciones y variables, información de tipo y ubicaciones de números de línea para su uso por el depurador. Esta información de depuración simbólica puede incluirse en los archivos objeto (archivos. obj) generados por el compilador o en un archivo PDB independiente (un archivo. pdb) para el ejecutable.  Las opciones de formato de información de depuración se describen en las secciones siguientes.

### <a name="none"></a>None

De forma predeterminada, si no se especifica ninguna opción de formato de información de depuración, el compilador no genera ninguna información de depuración, por lo que la compilación es más rápida.

### <a name="z7"></a>/Z7

La opción **/Z7** genera archivos objeto que también contienen información de depuración simbólica completa para su uso con el depurador. Estos archivos objeto y el ejecutable compilado pueden ser mucho mayores que los archivos que no tienen información de depuración. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea. No se produce ningún archivo PDB.

En el caso de los distribuidores de versiones de depuración de bibliotecas de terceros, existe una ventaja de no tener un archivo PDB. Sin embargo, los archivos objeto de cualquier encabezado precompilado son necesarios durante la fase de vinculación de la biblioteca y para la depuración. Si solo hay información de tipo (y ningún código) en el archivo de objeto. PCH, también debe usar la opción [/YL (Insertar referencia PCH para biblioteca de depuración)](yl-inject-pch-reference-for-debug-library.md) , que está habilitada de forma predeterminada, al compilar la biblioteca.

La opción [/GM (habilitar recompilación mínima)](gm-enable-minimal-rebuild.md) en desuso no está disponible cuando se especifica **/Z7** .

### <a name="zi"></a>/ZI

La opción **/Zi** genera un archivo PDB independiente que contiene toda la información de depuración simbólica que se usa con el depurador. La información de depuración no se incluye en los archivos de objeto o el archivo ejecutable, lo que hace que sean mucho más pequeños.

El uso de **/Zi** no afecta a las optimizaciones. Sin embargo, **/Zi** implica **/Debug**; vea [/debug (generar información de depuración)](debug-generate-debug-info.md) para obtener más información.

Al especificar **/Zi** y **/CLR**, el atributo <xref:System.Diagnostics.DebuggableAttribute> no se coloca en los metadatos del ensamblado. Si lo desea, debe especificarlo en el código fuente. Este atributo puede afectar al rendimiento de la aplicación en tiempo de ejecución. Para obtener más información sobre cómo el atributo **depurable** afecta al rendimiento y cómo puede modificar el impacto en el rendimiento, vea [facilitar la depuración de una imagen](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

El compilador nombra el archivo PDB *Project*. pdb. Si compila un archivo fuera de un proyecto, el compilador crea un archivo PDB denominado VC*x*. pdb, donde *x* es una concatenación del número de versión principal y secundaria de la versión del compilador en uso. El compilador incrusta el nombre del archivo PDB y una firma con marca de tiempo de identificación en cada archivo objeto creado con esta opción, que apunta al depurador a la ubicación de la información simbólica y de número de línea. El nombre y la firma del archivo PDB deben coincidir con el ejecutable de los símbolos que se van a cargar en el depurador. El depurador WinDBG puede cargar símbolos no coincidentes mediante el comando `.symopt+0x40`. Visual Studio no tiene una opción similar para cargar símbolos no coincidentes.

Si crea una biblioteca a partir de objetos compilados mediante **/Zi**, el archivo. pdb asociado debe estar disponible cuando la biblioteca esté vinculada a un programa. Por lo tanto, si distribuye la biblioteca, también debe distribuir el archivo PDB. Para crear una biblioteca que contenga información de depuración sin usar archivos PDB, debe seleccionar la opción **/Z7** . Si utiliza las opciones de encabezados precompilados, la información de depuración para el encabezado precompilado y el resto del código fuente se colocan en el archivo PDB.

### <a name="zi"></a>/ZI

La opción **/Zi** es similar a **/Zi**, pero genera un archivo PDB en un formato que admite la característica [Editar y continuar](/visualstudio/debugger/edit-and-continue-visual-cpp) . Para usar las características de depuración editar y continuar, debe usar esta opción. La característica editar y continuar es útil para la productividad de los desarrolladores, pero puede causar problemas en el tamaño del código, el rendimiento y el cumplimiento del compilador. Dado que la mayoría de las optimizaciones son incompatibles con editar y continuar, el uso de **/Zi** deshabilita cualquier instrucción `#pragma optimize` del código. La opción **/Zi** también es incompatible con el uso de [ &#95; &#95;la&#95; &#95; macro predefinida de línea](../../preprocessor/predefined-macros.md); el código compilado con **/Zi** no **&#95; &#95;puede&#95;** usar la línea como argumento de plantilla sin tipo, aunque **&#95; &#95;&#95;** se puede usar la línea en las expansiones de macro.

La opción **/Zi** fuerza las opciones [/GY (habilitar vinculación en el nivel de función)](gy-enable-function-level-linking.md) y [/FC (ruta de acceso completa de archivo de código fuente en diagnósticos)](fc-full-path-of-source-code-file-in-diagnostics.md) que se van a usar en la compilación.

**/Zi** no es compatible con [/CLR (compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> La opción **/Zi** solo está disponible en los compiladores que tienen como destino procesadores x86 y x64. Esta opción del compilador no está disponible en los compiladores que tienen como destino Procesadores ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra las **propiedades de configuración** > página de propiedades **General** de **CC++ /**  > .

1. Modifique la propiedad formato de la **información de depuración** . Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
