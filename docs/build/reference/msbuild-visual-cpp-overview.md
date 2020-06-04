---
title: Parámetros internos de MSBuild para proyectos de C++ en Visual Studio
ms.date: 02/26/2020
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: 010fa244ed77ea782fa76be959c58ff1e1b254a9
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166724"
---
# <a name="msbuild-internals-for-c-projects"></a>Parámetros internos de MSBuild para proyectos de C++

Cuando se establecen las propiedades del proyecto en el IDE y después se guarda el proyecto, Visual Studio escribe la configuración del proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto. Sin embargo, no contiene todos los valores necesarios para compilar el proyecto. El archivo de proyecto contiene elementos `Import` que incluyen una red de *archivos auxiliares* adicionales. Los archivos de compatibilidad contienen las propiedades, destinos y valores de configuración restantes necesarios para compilar el proyecto.

La mayoría de los destinos y propiedades de los archivos auxiliares existen solamente para implementar el sistema de compilación. En este artículo se describen las propiedades y los destinos útiles que se pueden especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos de los directorios de archivos auxiliares.

## <a name="support-file-directories"></a>Directorios de archivos auxiliares

De forma predeterminada, los principales archivos auxiliares de Visual Studio se encuentran en los directorios siguientes. Esta información es específica de la versión.

### <a name="visual-studio-2019"></a>Visual Studio 2019

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*versión*\\VCTargets\\

  Contiene los principales archivos de destino (.targets) y de propiedades (.props) que usan los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio. El marcador de posición de la *versión* hace referencia a la versión de Visual Studio: V160 para visual Studio 2019, V150 para visual Studio 2017.

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*versión*\\VCTargets\\plataformas\\*plataforma*\\

  Contiene los archivos de destinos y propiedades específicos de la plataforma que invalidan los destinos y las propiedades en su directorio principal. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64.

- % VSINSTALLDIR% MSBuild\\Microsoft\\VC\\*versión*\\VCTargets\\plataformas\\*plataforma*\\PlatformToolsets\\*conjunto de herramientas*\\

  Contiene los directorios que permiten a la compilación generar aplicaciones C++ mediante el *conjunto de herramientas* especificado. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64. El marcador de posición del *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas.

### <a name="visual-studio-2017"></a>Visual Studio 2017

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\

  Contiene los principales archivos de destino (.targets) y de propiedades (.props) que usan los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio.

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\plataformas\\*plataforma*\\

  Contiene los archivos de destinos y propiedades específicos de la plataforma que invalidan los destinos y las propiedades en su directorio principal. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64.

- % VSINSTALLDIR% Common7\\IDE\\VC\\VCTargets\\plataformas\\*plataforma*\\PlatformToolsets\\*conjunto de herramientas*\\

  Contiene los directorios que permiten a la compilación generar aplicaciones C++ mediante el *conjunto de herramientas* especificado. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64. El marcador de posición del *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas.

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 y anterior

- *unidad*:\\archivos de programa *(x86)* \\MSBuild\\Microsoft. Cpp (x86)\\v 4.0\\*versión*\\

  Contiene los principales archivos de destino (.targets) y de propiedades (.props) que usan los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio.

- *unidad*:\\archivos de programa *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0 *\\plataformas\\* *plataforma*\\\\

  Contiene los archivos de destinos y propiedades específicos de la plataforma que invalidan los destinos y las propiedades en su directorio principal. Este directorio también contiene un archivo DLL que define las tareas que se usan en los destinos de este directorio. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64.

- *unidad*:\\archivos de programa *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0 *\\plataformas\\* \\*plataforma*\\PlatformToolsets\\*conjunto de herramientas*\\

  Contiene los directorios que permiten a la compilación generar aplicaciones C++ mediante el *conjunto de herramientas* especificado. El marcador de posición de la *versión* es V110 para visual Studio 2012, V120 para Visual Studio 2013 y V140 para visual Studio 2015. El marcador de posición *plataforma* representa el subdirectorio ARM, Win32 o x64. El marcador de posición del *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas. Por ejemplo, es V140 para compilar aplicaciones de Windows mediante el conjunto de herramientas 2015 de Visual Studio. O bien, v120_xp para compilar para Windows XP con el conjunto de herramientas Visual Studio 2013.

- *unidad*:\\archivos de programa *(x86)* \\MSBuild\\Microsoft. Cpp\\v 4.0\\plataformas\\*plataforma*\\PlatformToolsets\\*conjunto de herramientas*\\

  Las rutas de acceso que permiten a la compilación generar aplicaciones de Visual Studio 2008 o Visual Studio 2010 no incluyen la *versión*. En esas versiones, el marcador de posición de la *plataforma* representa el subdirectorio Itanium, Win32 o x64. El marcador de posición *conjunto de herramientas* representa el subdirectorio del conjunto de herramientas v90 o v100.

## <a name="support-files"></a>Archivos auxiliares

Los directorios de archivos auxiliares contienen archivos con estas extensiones:

| Extensión | Descripción |
| --------- | ----------- |
| .targets | Contiene elementos XML `Target` que especifican las tareas que ejecuta el destino. También puede contener elementos `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup` y `Item` definidos por el usuario que se usan para asignar archivos y opciones de la línea de comandos a los parámetros de tarea.<br /><br /> Para más información, vea [Elemento Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild). |
| .props | Contiene los elementos XML `Property Group` y `Property` definidos por el usuario que especifican los valores de archivo y parámetros que se usan durante una compilación.<br /><br /> También puede contener los elementos XML `ItemDefinitionGroup` y `Item` definido por el usuario que especifican opciones de configuración adicionales. Los elementos definidos en un grupo de definiciones de elemento se parecen a las propiedades, pero no se puede tener acceso a ellos desde la línea de comandos. En los archivos de proyecto de Visual Studio se usan con frecuencia elementos en lugar de propiedades para representar valores.<br /><br /> Para obtener más información, vea [elemento ItemGroup (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [elemento ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)y elemento [Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild). |
| .xml | Contiene elementos XML que declaran e inicializan los elementos de la interfaz de usuario del IDE. Por ejemplo, las hojas de propiedades, las páginas de propiedades, los controles TextBox y los controles ListBox.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Pero los valores de propiedades del IDE se asignan a propiedades y elementos de compilación.<br /><br /> La mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, los archivos de la región Spanish-US se encuentran en $ (VCTargetsPath)\\1033\\. |

## <a name="user-targets-and-properties"></a>Propiedades y destinos del usuario

Para usar MSBuild de forma eficaz, ayuda a saber qué propiedades y destinos son útiles y relevantes. La mayoría de las propiedades y los destinos ayudan a implementar el sistema de compilación de Visual Studio y, por tanto, no son relevantes para el usuario. En esta sección se describen las propiedades orientadas al usuario y los destinos que merece la pena conocer.

### <a name="platformtoolset-property"></a>PlatformToolset (propiedad)

La propiedad `PlatformToolset` determina qué conjunto de herramientas de MSVC se usa en la compilación. De forma predeterminada, se usa el conjunto de herramientas actual. Cuando se establece esta propiedad, su valor se concatena con cadenas literales para formar la ruta de acceso. Es el directorio que contiene los archivos de destino y de propiedad necesarios para compilar un proyecto para una plataforma determinada. Se debe instalar el conjunto de herramientas de la plataforma para poder compilar con esa versión del conjunto de herramientas de la plataforma.

Por ejemplo, establezca la propiedad `PlatformToolset` en `v140` para usar las herramientas y bibliotecas de Visual Studio 2015 para compilar la aplicación:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture (propiedad)

La propiedad `PreferredToolArchitecture` determina si en la compilación se usan el compilador y las herramientas de 32 bits o 64 bits. Esta propiedad no afecta a la configuración o la arquitectura de la plataforma de salida. De forma predeterminada, MSBuild usa la versión x86 del compilador y las herramientas si esta propiedad no está establecida.

Por ejemplo, establezca la propiedad `PreferredToolArchitecture` en `x64` para usar el compilador y las herramientas de 64 bits para compilar la aplicación:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv (propiedad)

De forma predeterminada, la configuración específica de la plataforma para el proyecto actual invalida las variables de entorno PATH, INCLUDE, LIB, LIBPATH, CONFIGURATION y PLATFORM. Establezca la propiedad `UseEnv` en **true** para garantizar que las variables de entorno no se invaliden.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Destinos

En los archivos auxiliares de Visual Studio hay centenares de destinos. Pero la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos del sistema llevan como prefijo un carácter de subrayado (`_`), o tienen un nombre que empieza por "PrepareFor", "Compute", "Before", "after", "pre" o "post".

En la tabla siguiente se enumeran varios destinos útiles orientados al usuario.

| Destino | Descripción |
| ------ | ----------- |
| BscMake | Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe. |
| Build | Compila el proyecto.<br /><br /> Este destino es el valor predeterminado para un proyecto de. |
| ClCompile | Ejecuta la herramienta del compilador MSVC, cl.exe. |
| Clean | Elimina los archivos de compilación temporales e intermedios. |
| Lib | Ejecuta la herramienta del Administrador de bibliotecas de Microsoft de 32 bits, lib.exe. |
| Vínculo | Ejecuta la herramienta del enlazador de MSVC, link.exe. |
| ManifestResourceCompile | Extrae una lista de recursos de un manifiesto y, después, ejecuta la herramienta Compilador de recursos de Microsoft Windows, rc.exe. |
| Midl | Ejecuta la herramienta de compilador Lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe. |
| Volver a generar | Limpia y después compila el proyecto. |
| ResourceCompile | Ejecuta la herramienta Compilador de recursos de Microsoft Windows rc.exe. |
| XdcMake | Ejecuta la herramienta de documentación XML, xdcmake.exe. |
| Xsd | Ejecuta la herramienta Definición de esquemas XML, xsd.exe. *Vea la nota siguiente.* |

> [!NOTE]
> En Visual Studio 2017 y versiones posteriores, la compatibilidad con los archivos **xsd** en proyectos de C++ está en desuso. Puede seguir usando **Microsoft.VisualC.CppCodeProvider** si agrega manualmente **CppCodeProvider.dll** a la GAC.

## <a name="see-also"></a>Consulte también

\ de [referencia de tareas de MSBuild](/visualstudio/msbuild/msbuild-task-reference)
\ de [tareas de BSCMAKE](/visualstudio/msbuild/bscmake-task)
\ de [tareas de cl](/visualstudio/msbuild/cl-task)
\ de [tareas cppclean (](/visualstudio/msbuild/cppclean-task)
\ de [tareas de lib](/visualstudio/msbuild/lib-task)
\ de [tareas de vínculo](/visualstudio/msbuild/link-task)
\ de [tareas de MIDL](/visualstudio/msbuild/midl-task)
\ de [tareas de MT](/visualstudio/msbuild/mt-task)
\ de [tareas RC](/visualstudio/msbuild/rc-task)
[Tarea SetEnv](/visualstudio/msbuild/setenv-task)\
\ de [tareas VCMessage](/visualstudio/msbuild/vcmessage-task)
[Tarea XDCMake](/visualstudio/msbuild/xdcmake-task)
