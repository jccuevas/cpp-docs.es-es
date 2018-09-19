---
title: Información general sobre MSBuild (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad6feef707d991d07fa4e086bc8535f32b991825
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716877"
---
# <a name="msbuild-visual-c-overview"></a>Información general sobre MSBuild (Visual C++)

MSBuild es el estándar de sistema de compilación para proyectos de Visual C++. Cuando compila un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, usa la herramienta msbuild.exe, un archivo de proyecto basado en XML y archivos de configuración opcionales. Aunque puede utilizar msbuild.exe y un archivo de proyecto en la línea de comandos, el IDE proporciona una interfaz de usuario para que se puede configurar más fácilmente y compilar un proyecto. Esta introducción describe cómo Visual C++ utiliza el sistema MSBuild.

## <a name="prerequisites"></a>Requisitos previos

Lea los siguientes documentos sobre MSBuild.

- [MSBuild](/visualstudio/msbuild/msbuild) conceptos de información general de MSBuild.

- [Referencia de MSBuild](/visualstudio/msbuild/msbuild-reference) hacen referencia a información sobre el sistema MSBuild.

- [Referencia de esquema de archivo de proyecto](/visualstudio/msbuild/msbuild-project-file-schema-reference) se enumeran los elementos de esquema XML de MSBuild, junto con sus atributos y elementos primarios y secundarios. Observe especialmente el [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [destino](/visualstudio/msbuild/target-element-msbuild), y [tarea](/visualstudio/msbuild/task-element-msbuild) elementos.

- [Referencia de línea de comandos](/visualstudio/msbuild/msbuild-command-line-reference) se describen los argumentos de línea de comandos y opciones que puede utilizar con msbuild.exe.

- [Referencia de tareas](/visualstudio/msbuild/msbuild-task-reference) las tareas de MSBuild describe. Tenga en cuenta especialmente estas tareas, que son específicas de Visual C++: [tarea BscMake](/visualstudio/msbuild/bscmake-task), [CL (tarea)](/visualstudio/msbuild/cl-task), [CPPClean (tarea)](/visualstudio/msbuild/cppclean-task), [LIB (tarea)](/visualstudio/msbuild/lib-task), [Vincular tarea](/visualstudio/msbuild/link-task), [MIDL (tarea)](/visualstudio/msbuild/midl-task), [MT (tarea)](/visualstudio/msbuild/mt-task), [tarea RC](/visualstudio/msbuild/rc-task), [SetEnv (tarea)](/visualstudio/msbuild/setenv-task), [ Tarea VCMessage](/visualstudio/msbuild/vcmessage-task), [XDCMake (tarea)](/visualstudio/msbuild/xdcmake-task), [XSD (tarea)](/visualstudio/msbuild/xsd-task).

## <a name="msbuild-on-the-command-line"></a>MSBuild en la línea de comandos

La siguiente instrucción desde el [referencia de línea de comandos de MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) muestra que la herramienta msbuild.exe toma un implícita o explícita *project_file* argumento (un archivo .vcxproj para los proyectos de Visual C++) y cero o más de línea de comandos *opciones* argumentos.

> **MSBuild.exe** [ *project_file* ] [ *opciones* ]

Use la **/target** (o **/t**) y **/Property** (o **/p**) opciones de línea de comandos para invalidar los destinos y propiedades específicas Si se especifica en el archivo de proyecto.

Es una función esencial del archivo del proyecto especificar un *destino*, que es una operación determinada aplicada a su proyecto y las entradas y salidas que son necesarios para realizar esa operación. Un archivo de proyecto puede especificar uno o varios destinos, que pueden incluir un destino predeterminado.

Cada destino consta de una secuencia de uno o varios *tareas*. Cada tarea se representa mediante una clase de .NET Framework que contiene un comando ejecutable. Por ejemplo, el [CL (tarea)](/visualstudio/msbuild/cl-task) contiene el [cl.exe](../build/reference/compiling-a-c-cpp-program.md) comando.

Un *parámetro de tarea* es una propiedad de la tarea de la clase y que normalmente representa una opción de línea de comandos del comando ejecutable. Por ejemplo, el `FavorSizeOrSpeed` parámetro de la `CL` tarea corresponde a la **/Os** y **/Ot** opciones del compilador.

Parámetros de tarea adicionales admiten la infraestructura de MSBuild. Por ejemplo, el `Sources` parámetro de tarea Especifica un conjunto de tareas que pueden usarse en otras tareas. Para obtener más información acerca de las tareas de MSBuild, vea [referencia de tareas](/visualstudio/msbuild/msbuild-task-reference).

Mayoría de las tareas requiere entradas y salidas, como cadena, numéricos o booleanos parámetros, las rutas de acceso y nombres de archivo. Por ejemplo, una entrada habitual es el nombre de un archivo de código fuente .cpp para compilar. Un parámetro de entrada importante es una cadena que especifica la configuración de compilación y plataforma, por ejemplo, "depurar\|Win32". Las entradas y salidas se especifican mediante uno o varios XML definido por el usuario `Item` elementos contenidos en un `ItemGroup` elemento.

También puede especificar un archivo de proyecto definido por el usuario *propiedades* y `ItemDefinitionGroup` *elementos*. Las propiedades y los elementos forman pares de nombre/valor que se pueden usar como variables en la compilación. El componente de nombre de un par define una *macro*, y el componente de valor declara el *el valor de macro*. Se tiene acceso a una macro de propiedad mediante el uso de $(*nombre*) notación y una macro de elemento que se accede mediante %(*nombre*) notación.

Otros elementos XML en un archivo de proyecto pueden probar las macros y, a continuación, condicionalmente establezca el valor de una macro o controlar la ejecución de la compilación. Los nombres de macro y cadenas literales se pueden concatenar para generar estructuras como un ruta de acceso y nombre de archivo. En la línea de comandos, el **/Property** opción establece o invalida una propiedad de proyecto. No se pueden hacer referencia a elementos en la línea de comandos.

El sistema MSBuild puede ejecutar condicionalmente un destino antes o después de otro destino. Además, el sistema puede crear un destino en función de si los archivos que usa el destino son más recientes que los archivos que emite.

## <a name="msbuild-in-the-ide"></a>MSBuild en el IDE

Al establecer las propiedades del proyecto en el IDE y, a continuación, guarde el proyecto, Visual C++ escribe la configuración del proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto, pero no contiene toda la configuración necesarios para compilar el proyecto. Contiene el archivo de proyecto `Import` elementos que incluyen una red de adicionales *archivos auxiliares.* Los archivos de compatibilidad contienen las restantes propiedades, destinos y valores de configuración necesarios para compilar el proyecto.

La mayoría de los destinos y propiedades de los archivos de compatibilidad existen solamente para implementar el sistema de compilación. La siguiente sección describe algunos destinos y propiedades útiles que se pueden especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos en los directorios de archivos de soporte técnico.

### <a name="support-file-directories"></a>Directorios de archivos de soporte técnico

De forma predeterminada, los archivos de soporte técnico principales de Visual C++ se encuentran en los siguientes directorios. Visual Studio 2017 y versiones posteriores, utiliza los directorios en Microsoft Visual Studio aunque Visual Studio 2015 y versiones anteriores usan los directorios en MSBuild.

|Directorio|Descripción|
|---------------|-----------------|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*versión*\ |Contiene los archivos de destino principal (.targets) y archivos de propiedad (.props) que se utilizan en los destinos. De forma predeterminada, la macro VCTargetsPath hace referencia a este directorio.|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ |Contiene los archivos específicos de la plataforma de destino y propiedad que invalidan los destinos y propiedades de su directorio primario. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio.<br /><br /> El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio.|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ |Contiene los directorios que permiten a la compilación generar aplicaciones de Visual C++ mediante la interfaz *toolset*.<br /><br /> El *año* y *edition* utilizan marcadores de posición Visual Studio 2017 y ediciones posteriores. El *versión* marcador de posición es V110 para Visual Studio 2012, V120 para Visual Studio 2013 o V140 para Visual Studio 2015. El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio. El *toolset* marcador de posición representa el subdirectorio del conjunto de herramientas, por ejemplo, v140 para compilar aplicaciones de Windows con el conjunto de herramientas de Visual Studio 2015, v120_xp para crear aplicaciones para XP de Windows con el conjunto de herramientas de Visual Studio 2013 o v110_wp80 a compilar aplicaciones de Windows Phone 8.0 con el conjunto de herramientas de Visual Studio 2012.<br /><br />La ruta de acceso que contiene los directorios que permiten a la compilación generar aplicaciones de Visual C++ 2008 o Visual C++ 2010 no incluye el *versión*y el *plataforma* representa el marcador de posición el procesador Itanium, Win32 o x64 subdirectorio. El *toolset* marcador de posición representa el subdirectorio del conjunto de herramientas v90 o v100.|

### <a name="support-files"></a>Archivos de compatibilidad

Los directorios de archivos de compatibilidad contienen archivos con estas extensiones:

|Comprobación de actualización|Descripción|
|---------------|-----------------|
|.targets|Contiene `Target` elementos XML que especifican las tareas que se ejecutan en el destino. También puede contener `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`y definido por el usuario `Item` elementos que se usan para asignar archivos y opciones de línea de comandos a los parámetros de tarea.<br /><br /> Para obtener más información, consulte [elemento Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Contiene `Property Group` y definido por el usuario `Property` elementos XML que especifican los valores de archivo y los parámetros que se usan durante una compilación.<br /><br /> También puede contener `ItemDefinitionGroup` y definido por el usuario `Item` elementos XML que especifican opciones de configuración adicionales. Los elementos definidos en un grupo de definiciones de elemento son similares a las propiedades, pero no es accesible desde la línea de comandos. Archivos de proyecto de Visual C++, se utiliza con frecuencia elementos en lugar de propiedades para representar los valores.<br /><br /> Para obtener más información, consulte [elemento ItemGroup (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [elemento ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), y [elemento Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.Xml|Contiene elementos XML que declaran e inicializan elementos de interfaz de usuario del IDE como hojas de propiedades y páginas de propiedades y los controles de cuadro de lista y el cuadro de texto.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Sin embargo, los valores de propiedades del IDE se asignan a las propiedades y elementos de compilación.<br /><br /> Mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, los archivos para la región de inglés de Estados Unidos se encuentran en $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Las propiedades y destinos de usuarios

Para utilizar MSBuild de la forma más eficaz en la línea de comandos, conviene para saber qué propiedades y destinos son útiles y pertinentes. La mayoría de las propiedades y destinos ayudan a implementar el sistema de compilación de Visual C++ y, por lo tanto, no son relevantes para el usuario. Esta sección describen algunos objetivos y merece la pena propiedades orientadas al usuario.

### <a name="platformtoolset-property"></a>Propiedad PlatformToolset

El `PlatformToolset` propiedad determina qué conjunto de herramientas de Visual C++ se usa en la compilación. De forma predeterminada, se usa el conjunto de herramientas actual. Cuando se establece esta propiedad, el valor de la propiedad se concatena con cadenas literal para formar la ruta de acceso de un directorio que contiene los archivos de destino y propiedad necesarios para compilar un proyecto para una plataforma concreta. Debe instalarse el conjunto de herramientas de plataforma para compilar con esa versión del conjunto de herramientas de plataforma.

Por ejemplo, establecer el `PlatformToolset` propiedad `v140` usar bibliotecas y herramientas de Visual C++ 2015 para compilar la aplicación:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Propiedad PreferredToolArchitecture

El `PreferredToolArchitecture` propiedad determina si el compilador de 32 bits o 64 bits y las herramientas se utilizan en la compilación. Esta propiedad no afecta a la arquitectura de la plataforma de salida o la configuración. De forma predeterminada, MSBuild usa el x86 versión del compilador y herramientas si no se establece esta propiedad.

Por ejemplo, establecer el `PreferredToolArchitecture` propiedad `x64` para usar el compilador de 64 bits y herramientas para compilar la aplicación:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Propiedad UseEnv

De forma predeterminada, la configuración de específicos de la plataforma para el proyecto actual invalida las variables de entorno PATH, INCLUDE, LIB, LIBPATH, configuración y plataforma. Establecer el `UseEnv` propiedad `true` para garantizar que no se invalidan las variables de entorno.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Destinos

Hay centenares de destinos en los archivos de compatibilidad de Visual C++. Sin embargo, la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos de sistema están precedidos por un carácter de subrayado (_) o tienen un nombre que comienza con "PrepareFor", "Compute", "Before", "After", "Pre" o "Post".

En la tabla siguiente se enumera varios destinos útiles orientado al usuario.

|Destino|Descripción|
|------------|-----------------|
|BscMake|Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe.|
|Compilar|Compila el proyecto.<br /><br /> Este es el destino predeterminado para un proyecto.|
|ClCompile|Ejecuta la herramienta de compilador de Visual C++, cl.exe.|
|Limpiar|Crear archivos de eliminaciones temporales e intermedios.|
|Lib|Ejecuta la herramienta Administrador de bibliotecas de Microsoft de 32 bits, lib.exe.|
|Vínculo|Ejecuta la herramienta del vinculador de Visual C++, link.exe.|
|ManifestResourceCompile|Extrae una lista de recursos de un manifiesto y, a continuación, ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|
|MIDL|Ejecuta la herramienta compilador de lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe.|
|Recompilar|Limpia y, a continuación, compila el proyecto.|
|ResourceCompile|Ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|
|XdcMake|Ejecuta la herramienta de documentación XML, xdcmake.exe.|
|XSD|Ejecuta la herramienta de definición de esquemas XML, xsd.exe. *Vea la nota siguiente.*|

> [!NOTE]
> En Visual Studio 2017, proyecto de compatibilidad con C++ **xsd** archivos está en desuso. Todavía puede usar **Microsoft.VisualC.CppCodeProvider** agregando **CppCodeProvider.dll** manualmente a la GAC.

## <a name="see-also"></a>Vea también

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
