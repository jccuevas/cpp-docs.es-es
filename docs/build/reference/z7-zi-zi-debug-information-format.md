---
title: "-Z7, - Zi, - ZI (formato de la información de depuración) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b55c5ea77b752d4adac8d74abaed245b4d19821
ms.sourcegitcommit: 3038840ca6e4dea01accf733436b99d19ff6c930
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Formato de la información de depuración)

Especifica el tipo de información de depuración creada para el programa y si esta información se conserva en archivos objeto o en un archivo de programa (PDB) de la base de datos.

## <a name="syntax"></a>Sintaxis

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>Comentarios

Cuando el código se compila y se compila en modo de depuración, el compilador genera nombres de símbolos para las funciones y variables, información de tipo y ubicaciones de número de línea para su uso por el depurador. Esta información de depuración simbólica pueden incluir en los archivos de objeto (archivos .obj) generados por el compilador, o en un archivo PDB independiente (un archivo .pdb) para el archivo ejecutable.  Las opciones de formato de la información de depuración se describen en las secciones siguientes.  
  
### <a name="none"></a>Ninguna

De forma predeterminada, si no se especifica ninguna opción de formato de información de depuración, el compilador no genera ninguna información de depuración, por lo que la compilación es más rápida.  
  
### <a name="z7"></a>/Z7

El **/Z7** opción genera archivos de objeto que también contienen información de depuración simbólica completa para su uso con el depurador. Estos archivos de objeto y el ejecutable generado pueden ser considerablemente mayores que los archivos que no tengan ninguna información de depuración. La información de depuración simbólica incluye los nombres y los tipos de las variables, así como las funciones y los números de línea. No se genera ningún archivo PDB.

Para los distribuidores de versiones de depuración de bibliotecas de otros fabricantes, hay una ventaja a no tener un archivo PDB. Sin embargo, los archivos de objeto para los encabezados precompilados son necesarios durante la fase de vinculación de biblioteca y para la depuración. Si sólo hay tipo información (y ningún código) en el archivo de objeto .pch, también debe usar el [/Yl (Insertar referencia PCH para biblioteca de depuración)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) opción, que está habilitada de forma predeterminada, cuando se compila la biblioteca.

El [/Gm (habilitar recompilación mínima)](../../build/reference/gm-enable-minimal-rebuild.md) opción no está disponible cuando **/Z7** se especifica.

### <a name="zi"></a>/ZI

El **/Zi** opción genera un archivo PDB independiente que contiene todos los la depuración información simbólica para su uso con el depurador. La información de depuración no está incluida en los archivos objeto o ejecutable, lo que hace que sean mucho más pequeño.

El uso de **/Zi** no afecta a las optimizaciones. Sin embargo, **/Zi** implica **/debug**; vea [/DEBUG (generar información de depuración)](../../build/reference/debug-generate-debug-info.md) para obtener más información.


Al especificar ambos **/Zi** y **/CLR**, el <xref:System.Diagnostics.DebuggableAttribute> atributo no se coloca en los metadatos del ensamblado. Si desea, debe especificar en el código fuente. Este atributo puede afectar al rendimiento de la aplicación en tiempo de ejecución. Para obtener más información acerca de cómo los **atributo Debuggable** atributo afecta al rendimiento y cómo puede modificar el impacto en el rendimiento, vea [facilitar una imagen para depuración](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

El compilador nombre al archivo PDB *proyecto*.pdb. Si compila un archivo fuera de un proyecto, el compilador crea un archivo PDB, denominado VC*x*archivo .pdb, donde *x* es una concatenación del número de versión principal y secundaria de la versión del compilador en uso. El compilador incrusta el nombre de la PDB y una identificación firma con marca de tiempo en cada archivo de objeto creado con esta opción, que señala al depurador a la ubicación de la información simbólica y número de línea. El nombre y la firma en el archivo PDB deben coincidir con el archivo ejecutable para símbolos que se va a cargar en el depurador. El depurador WinDBG puede cargar los símbolos que no coincidan utilizando el `.symopt+0x40` comando. Visual Studio no tiene una opción similar para cargar los símbolos que no coincidentes.

Si se crea una biblioteca de objetos que se compilaron con **/Zi**, el archivo .pdb asociado debe estar disponible cuando la biblioteca está vinculada a un programa. Por lo tanto, si distribuye la biblioteca, también debe distribuir el archivo PDB. Para crear una biblioteca que contiene información de depuración sin usar archivos PDB, debe seleccionar la **/Z7** opción. Si utiliza las opciones de encabezado precompilado, la información de depuración del encabezado precompilado y el resto del código fuente se coloca en el archivo PDB.

### <a name="zi"></a>/ZI

El **/Zi** opción es similar a **/Zi**, pero produce un archivo PDB en un formato que admita la [editar y continuar](/visualstudio/debugger/edit-and-continue-visual-cpp) característica. Para usar Editar y continuar características de depuración, debe usar esta opción. La característica Editar y continuar es útil para la productividad del desarrollador, pero puede causar problemas de ajuste de tamaño, el rendimiento y el compilador de código. Dado que la mayoría de las optimizaciones es incompatible con Editar y continuar, uso **/Zi** deshabilita cualquier `#pragma optimize` las instrucciones en el código. El **/Zi** opción también es compatible con el uso de la [&#95; &#95; LÍNEA &#95; &#95; macro predefinida](../../preprocessor/predefined-macros.md); código compilado con **/Zi** no se puede usar **&#95; &#95; LÍNEA &#95; &#95;**  como un argumento de plantilla sin tipo, aunque **&#95; &#95; LÍNEA &#95; &#95;**  puede utilizarse en expansiones de macros.

El **/Zi** opción obliga a ambos el [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) y [/FC (Full ruta de acceso del archivo de código fuente en diagnósticos)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) opciones que se utilizarán en la compilación.

**/ Zi** no es compatible con [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> El **/Zi** opción sólo está disponible en los compiladores con destino procesadores x86 y x64; esta opción del compilador no está disponible en los compiladores con destino procesadores ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Abra la **propiedades de configuración** > **C/C++** > **General** página de propiedades.

1. Modificar el **formato de información de depuración** propiedad. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  

