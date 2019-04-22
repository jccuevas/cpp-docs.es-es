---
title: Los proyectos de aspectos internos de MSBuild para C++ en Visual Studio
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 6c8e891f6bf6ed6b3bb3d1c84dbc13b64ab7b868
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021909"
---
# <a name="msbuild-internals-for-c-projects"></a>Parámetros internos de MSBuild para proyectos de C++

Al establecer las propiedades del proyecto en el IDE y, a continuación, guarde el proyecto, Visual Studio escribe la configuración del proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto, pero no contiene toda la configuración necesarios para compilar el proyecto. Contiene el archivo de proyecto `Import` elementos que incluyen una red de adicionales *archivos auxiliares.* Los archivos de compatibilidad contienen las restantes propiedades, destinos y valores de configuración necesarios para compilar el proyecto.

La mayoría de los destinos y propiedades de los archivos de compatibilidad existen solamente para implementar el sistema de compilación. La siguiente sección describe algunos destinos y propiedades útiles que se pueden especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos en los directorios de archivos de soporte técnico.

## <a name="support-file-directories"></a>Directorios de archivos de soporte técnico

De forma predeterminada, los archivos de soporte técnico principales de Visual Studio se encuentran en los siguientes directorios. Visual Studio 2017 y versiones posteriores, utiliza los directorios en Microsoft Visual Studio aunque Visual Studio 2015 y versiones anteriores usan los directorios en MSBuild.

|Directorio|Descripción|
|---------------|-----------------|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp (x86) \v4.0\\*versión*\ |Contiene los archivos de destino principal (.targets) y archivos de propiedad (.props) que se utilizan en los destinos. De forma predeterminada, la macro VCTargetsPath hace referencia a este directorio.|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ |Contiene los archivos específicos de la plataforma de destino y propiedad que invalidan los destinos y propiedades de su directorio primario. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio.<br /><br /> El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio.|
|*unidad*: \Program archivos *(x86)* \Microsoft Visual Studio\\*año*\\*edition*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)* \MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ |Contiene los directorios que permiten a la compilación generar aplicaciones de C++ mediante la interfaz *toolset*.<br /><br /> El *año* y *edition* utilizan marcadores de posición Visual Studio 2017 y ediciones posteriores. El *versión* marcador de posición es V110 para Visual Studio 2012, V120 para Visual Studio 2013 o V140 para Visual Studio 2015. El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio. El *toolset* marcador de posición representa el subdirectorio del conjunto de herramientas, por ejemplo, v140 para compilar aplicaciones de Windows con el conjunto de herramientas de Visual Studio 2015, v120_xp para crear aplicaciones para XP de Windows con el conjunto de herramientas de Visual Studio 2013 o v110_wp80 a compilar aplicaciones de Windows Phone 8.0 con el conjunto de herramientas de Visual Studio 2012.<br /><br />La ruta de acceso que contiene los directorios que permiten a la compilación generar aplicaciones de Visual Studio 2008 o Visual Studio 2010 no incluye el *versión*y el *plataforma* marcador de posición representa el procesador Itanium, Win32 o x64 subdirectorio. El *toolset* marcador de posición representa el subdirectorio del conjunto de herramientas v90 o v100.|

## <a name="support-files"></a>Archivos de compatibilidad

Los directorios de archivos de compatibilidad contienen archivos con estas extensiones:

|Comprobación de actualización|Descripción|
|---------------|-----------------|
|.targets|Contiene `Target` elementos XML que especifican las tareas que se ejecutan en el destino. También puede contener `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`y definido por el usuario `Item` elementos que se usan para asignar archivos y opciones de línea de comandos a los parámetros de tarea.<br /><br /> Para obtener más información, consulte [elemento Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|
|.props|Contiene `Property Group` y definido por el usuario `Property` elementos XML que especifican los valores de archivo y los parámetros que se usan durante una compilación.<br /><br /> También puede contener `ItemDefinitionGroup` y definido por el usuario `Item` elementos XML que especifican opciones de configuración adicionales. Los elementos definidos en un grupo de definiciones de elemento son similares a las propiedades, pero no es accesible desde la línea de comandos. Los archivos de proyecto de Visual Studio usan con frecuencia elementos en lugar de propiedades para representar los valores.<br /><br /> Para obtener más información, consulte [elemento ItemGroup (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), 
[Elemento ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), y [elemento Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|
|.xml|Contiene elementos XML que declaran e inicializan elementos de interfaz de usuario del IDE como hojas de propiedades y páginas de propiedades y los controles de cuadro de lista y el cuadro de texto.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Sin embargo, los valores de propiedades del IDE se asignan a las propiedades y elementos de compilación.<br /><br /> Mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, los archivos para la región de inglés de Estados Unidos se encuentran en $(VCTargetsPath) \1033\\.|

## <a name="user-targets-and-properties"></a>Las propiedades y destinos de usuarios

Para utilizar MSBuild de la forma más eficaz en la línea de comandos, conviene para saber qué propiedades y destinos son útiles y pertinentes. La mayoría de las propiedades y destinos ayudan a implementar el sistema de compilación de Visual Studio y, por lo tanto, no son relevantes para el usuario. Esta sección describen algunos objetivos y merece la pena propiedades orientadas al usuario.

### <a name="platformtoolset-property"></a>Propiedad PlatformToolset

El `PlatformToolset` propiedad determina qué conjunto de herramientas MSVC se utiliza en la compilación. De forma predeterminada, se usa el conjunto de herramientas actual. Cuando se establece esta propiedad, el valor de la propiedad se concatena con cadenas literal para formar la ruta de acceso de un directorio que contiene los archivos de destino y propiedad necesarios para compilar un proyecto para una plataforma concreta. Debe instalarse el conjunto de herramientas de plataforma para compilar con esa versión del conjunto de herramientas de plataforma.

Por ejemplo, establecer el `PlatformToolset` propiedad `v140` para usar las herramientas de Visual Studio 2015 y bibliotecas para compilar la aplicación:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>Propiedad PreferredToolArchitecture

El `PreferredToolArchitecture` propiedad determina si el compilador de 32 bits o 64 bits y las herramientas se utilizan en la compilación. Esta propiedad no afecta a la arquitectura de la plataforma de salida o la configuración. De forma predeterminada, MSBuild usa el x86 versión del compilador y herramientas si no se establece esta propiedad.

Por ejemplo, establecer el `PreferredToolArchitecture` propiedad `x64` para usar el compilador de 64 bits y herramientas para compilar la aplicación:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>Propiedad UseEnv

De forma predeterminada, la configuración de específicos de la plataforma para el proyecto actual invalida las variables de entorno PATH, INCLUDE, LIB, LIBPATH, configuración y plataforma. Establecer el `UseEnv` propiedad **true** para garantizar que no se invalidan las variables de entorno.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Destinos

Hay centenares de destinos en los archivos de compatibilidad de Visual Studio. Sin embargo, la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos de sistema están precedidos por un carácter de subrayado (_) o tienen un nombre que comienza con "PrepareFor", "Compute", "Before", "After", "Pre" o "Post".

En la tabla siguiente se enumera varios destinos útiles orientado al usuario.

|Destino|Descripción|
|------------|-----------------|
|BscMake|Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe.|
|Compilar|Compila el proyecto.<br /><br /> Este es el destino predeterminado para un proyecto.|
|ClCompile|Ejecuta la herramienta compilador MSVC, cl.exe.|
|Limpiar|Crear archivos de eliminaciones temporales e intermedios.|
|Lib|Ejecuta la herramienta Administrador de bibliotecas de Microsoft de 32 bits, lib.exe.|
|Link|Ejecuta la herramienta de vinculador MSVC, link.exe.|
|ManifestResourceCompile|Extrae una lista de recursos de un manifiesto y, a continuación, ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|
|MIDL|Ejecuta la herramienta compilador de lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe.|
|Volver a compilar|Limpia y, a continuación, compila el proyecto.|
|ResourceCompile|Ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|
|XdcMake|Ejecuta la herramienta de documentación XML, xdcmake.exe.|
|Xsd|Ejecuta la herramienta de definición de esquemas XML, xsd.exe. *Vea la nota siguiente.*|

> [!NOTE]
> En Visual Studio 2017, proyecto de compatibilidad con C++ **xsd** archivos está en desuso. Todavía puede usar **Microsoft.VisualC.CppCodeProvider** agregando **CppCodeProvider.dll** manualmente a la GAC.

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
