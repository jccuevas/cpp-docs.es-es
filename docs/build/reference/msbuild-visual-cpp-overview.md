---
title: Parámetros internos de MSBuild para proyectos de C++ en Visual Studio
ms.date: 05/16/2019
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: b3348320a1468fea03f39e43cc847f1085f3d319
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837226"
---
# <a name="msbuild-internals-for-c-projects"></a>Parámetros internos de MSBuild para proyectos de C++

Cuando se establecen las propiedades del proyecto en el IDE y después se guarda el proyecto, Visual Studio escribe la configuración del proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto, pero no contiene toda la configuración necesaria para compilar el proyecto. El archivo de proyecto contiene elementos `Import` que incluyen una red de *archivos auxiliares* adicionales. Los archivos auxiliares contienen las propiedades, destinos y valores de configuración restantes necesarios para compilar el proyecto.

La mayoría de los destinos y propiedades de los archivos auxiliares existen solamente para implementar el sistema de compilación. En la sección siguiente se describen algunos destinos y propiedades útiles que se pueden especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos de los directorios de archivos auxiliares.

## <a name="support-file-directories"></a>Directorios de archivos auxiliares

De forma predeterminada, los principales archivos auxiliares de Visual Studio se encuentran en los directorios siguientes. Los directorios de Microsoft Visual Studio se usan en Visual Studio 2017 y versiones posteriores, mientras que los de MSBuild se usan en Visual Studio 2015 y versiones anteriores.

|Directorio|Descripción|
|---------------|-----------------|
|*unidad*:\Archivos de programa *(x86)* \Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\ <br /><br />*unidad*:\Archivos de programa *(x86)* \MSBuild\Microsoft.Cpp (x86)\v4.0\\*versión*\ |Contiene los principales archivos de destino (.targets) y de propiedades (.props) que usan los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio.|
|*unidad*:\Archivos de programa *(x86)* \Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\Platforms\\*plataforma*\ <br /><br />*unidad*:\Archivos de programa *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ |Contiene los archivos de destinos y propiedades específicos de la plataforma que invalidan los destinos y las propiedades en su directorio principal. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio.<br /><br /> El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64.|
|*unidad*:\Archivos de programa *(x86)* \Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*:\Archivos de programa *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*:\Archivos de programa *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ |Contiene los directorios que permiten a la compilación generar aplicaciones C++ mediante el *conjunto de herramientas* especificado.<br /><br /> Los marcadores de posición *año* y *edición* se usan en Visual Studio 2017 y ediciones posteriores. El marcador de posición *versión* es V110 para Visual Studio 2012, V120 para Visual Studio 2013, V140 para Visual Studio 2015, v141 para Visual Studio 2017 y v142 para Visual Studio 2019. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64. El marcador de posición *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas, por ejemplo, v140 para compilar aplicaciones Windows con el conjunto de herramientas de Visual Studio 2015, v120_xp para compilar para Windows XP con el conjunto de herramientas de Visual Studio 2013.<br /><br />La ruta de acceso que contiene los directorios que permiten a la compilación generar aplicaciones de Visual Studio 2008 o Visual Studio 2010 no incluye la *versión*, y el marcador de posición *plataforma* representa el subdirectorio Itanium, Win32 o x64. El marcador de posición *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas v90 o v100.|

## <a name="support-files"></a>Archivos auxiliares

Los directorios de archivos auxiliares contienen archivos con estas extensiones:

|Comprobación de actualización|Descripción|
|---------------|-----------------|
|.targets|Contiene elementos XML `Target` que especifican las tareas que ejecuta el destino. También puede contener elementos `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup` y `Item` definidos por el usuario que se usan para asignar archivos y opciones de la línea de comandos a los parámetros de tarea.<br /><br /> Para más información, vea [Elemento Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Contiene los elementos XML `Property Group` y `Property` definidos por el usuario que especifican los valores de archivo y parámetros que se usan durante una compilación.<br /><br /> También puede contener los elementos XML `ItemDefinitionGroup` y `Item` definido por el usuario que especifican opciones de configuración adicionales. Los elementos definidos en un grupo de definiciones de elemento parecen propiedades, pero no son accesibles desde la línea de comandos. En los archivos de proyecto de Visual Studio se usan con frecuencia elementos en lugar de propiedades para representar valores.<br /><br /> Para más información, vea [Elemento ItemGroup (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[Elemento ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild) y [Elemento Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Contiene elementos XML que declaran e inicializan elementos de la interfaz de usuario del IDE como hojas de propiedades y páginas de propiedades, y los controles de cuadro de lista y cuadro de texto.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Pero los valores de propiedades del IDE se asignan a propiedades y elementos de compilación.<br /><br /> La mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, los archivos para la región inglés (Estados Unidos) se encuentran en $(VCTargetsPath)\1033\\.|

## <a name="user-targets-and-properties"></a>Propiedades y destinos del usuario

Para usar MSBuild de la forma más eficaz en la línea de comandos, conviene saber qué propiedades y destinos son útiles y pertinentes. La mayoría de las propiedades y los destinos facilitan la implementación del sistema de compilación de Visual Studio y, por tanto, no son relevantes para el usuario. En esta sección se describen algunos destinos y propiedades útiles orientados al usuario.

### <a name="platformtoolset-property"></a>PlatformToolset (propiedad)

La propiedad `PlatformToolset` determina qué conjunto de herramientas de MSVC se usa en la compilación. De forma predeterminada, se usa el conjunto de herramientas actual. Cuando se establece esta propiedad, su valor se concatena con cadenas literales para formar la ruta de acceso de un directorio que contiene los archivos de destinos y propiedades necesarios para compilar un proyecto para una plataforma concreta. Se debe instalar el conjunto de herramientas de la plataforma para poder compilar con esa versión del conjunto de herramientas de la plataforma.

Por ejemplo, establezca la propiedad `PlatformToolset` en `v140` para usar las herramientas y bibliotecas de Visual Studio 2015 para compilar la aplicación:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture (propiedad)

La propiedad `PreferredToolArchitecture` determina si en la compilación se usan el compilador y las herramientas de 32 bits o 64 bits. Esta propiedad no afecta a la arquitectura de la plataforma de salida ni a la configuración. Si no se establece esta propiedad, MSBuild usa de forma predeterminada la versión x86 del compilador y las herramientas.

Por ejemplo, establezca la propiedad `PreferredToolArchitecture` en `x64` para usar el compilador y las herramientas de 64 bits para compilar la aplicación:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv (propiedad)

De forma predeterminada, la configuración específica de la plataforma para el proyecto actual invalida las variables de entorno PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION y PLATFORM. Establezca la propiedad `UseEnv` en **true** para garantizar que las variables de entorno no se invaliden.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Destinos

En los archivos auxiliares de Visual Studio hay centenares de destinos. Pero la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos de sistema están precedidos por un carácter de subrayado (_) o tienen un nombre que comienza con "PrepareFor", "Compute", "Before", "After", "Pre" o "Post".

En la tabla siguiente se enumeran varios destinos útiles orientados al usuario.

|Destino|Descripción|
|------------|-----------------|
|BscMake|Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe.|
|Compilar|Compila el proyecto.<br /><br /> Es el destino predeterminado para un proyecto.|
|ClCompile|Ejecuta la herramienta del compilador MSVC, cl.exe.|
|Limpiar|Elimina los archivos de compilación temporales e intermedios.|
|Lib|Ejecuta la herramienta del Administrador de bibliotecas de Microsoft de 32 bits, lib.exe.|
|Link|Ejecuta la herramienta del enlazador de MSVC, link.exe.|
|ManifestResourceCompile|Extrae una lista de recursos de un manifiesto y, después, ejecuta la herramienta Compilador de recursos de Microsoft Windows, rc.exe.|
|Midl|Ejecuta la herramienta de compilador Lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe.|
|Volver a compilar|Limpia y después compila el proyecto.|
|ResourceCompile|Ejecuta la herramienta Compilador de recursos de Microsoft Windows rc.exe.|
|XdcMake|Ejecuta la herramienta de documentación XML, xdcmake.exe.|
|Xsd|Ejecuta la herramienta Definición de esquemas XML, xsd.exe. *Vea la nota siguiente.*|

> [!NOTE]
> En Visual Studio 2017 y versiones posteriores, la compatibilidad con los archivos **xsd** en proyectos de C++ está en desuso. Puede seguir usando **Microsoft.VisualC.CppCodeProvider** si agrega manualmente **CppCodeProvider.dll** a la GAC.

## <a name="see-also"></a>Vea también

[Referencia de tareas de MSBuild](/visualstudio/msbuild/msbuild-task-reference)<br/>
[Tarea BscMake](/visualstudio/msbuild/bscmake-task)<br/>
[Tarea CL](/visualstudio/msbuild/cl-task)<br/>
[Tarea CPPClean](/visualstudio/msbuild/cppclean-task)<br/>
[Tarea LIB](/visualstudio/msbuild/lib-task)<br/>
[Vincular tarea](/visualstudio/msbuild/link-task)<br/>
[Tarea MIDL](/visualstudio/msbuild/midl-task)<br/>
[Tarea MT](/visualstudio/msbuild/mt-task)<br/>
[Tarea RC](/visualstudio/msbuild/rc-task)<br/>
[Tarea SetEnv](/visualstudio/msbuild/setenv-task)<br/>
[Tarea VCMessage](/visualstudio/msbuild/vcmessage-task)<br/>
[Tarea XDCMake](/visualstudio/msbuild/xdcmake-task)<br/>
