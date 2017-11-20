---
title: "Información general sobre MSBuild (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2c238aabdfee5de1896e24934edee1ebec135be4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="msbuild-visual-c-overview"></a>Información general sobre MSBuild (Visual C++)  
  
MSBuild es el estándar de compilar el sistema de proyectos de Visual C++. Cuando se compila un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, utiliza la herramienta msbuild.exe, un archivo de proyecto basado en XML y archivos de configuración opcionales. Aunque puede utilizar msbuild.exe y un archivo de proyecto en la línea de comandos, el IDE proporciona una interfaz de usuario, por lo que puede configurar y compilar un proyecto más fácilmente. Esta introducción describe cómo Visual C++ utiliza el sistema de MSBuild.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
Lea los siguientes documentos sobre MSBuild.  
  
- [MSBuild](/visualstudio/msbuild/msbuild)  
 Información general de conceptos de MSBuild.  
  
- [Referencia de MSBuild](/visualstudio/msbuild/msbuild-reference)  
 Información de referencia sobre el sistema MSBuild.  
  
- [Referencia de esquemas de archivo del proyecto](/visualstudio/msbuild/msbuild-project-file-schema-reference)  
 Enumera los elementos de esquema XML de MSBuild, junto con sus atributos y los elementos primarios y secundarios. Observe especialmente la [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [destino](/visualstudio/msbuild/target-element-msbuild), y [tarea](/visualstudio/msbuild/task-element-msbuild) elementos.  
  
- [Referencia de la línea de comandos](/visualstudio/msbuild/msbuild-command-line-reference)  
 Describe los argumentos de línea de comandos y opciones que puede usar con msbuild.exe.  
  
- [Referencia de tareas](/visualstudio/msbuild/msbuild-task-reference)  
 Describe las tareas de MSBuild. Tenga en cuenta especialmente estas tareas, que son específicas de Visual C++: [BscMake (tarea)](/visualstudio/msbuild/bscmake-task), [CL (tarea)](/visualstudio/msbuild/cl-task), [CPPClean (tarea)](/visualstudio/msbuild/cppclean-task), [lib (tarea)](/visualstudio/msbuild/lib-task), [Vincular tarea](/visualstudio/msbuild/link-task), [MIDL (tarea)](/visualstudio/msbuild/midl-task), [MT (tarea)](/visualstudio/msbuild/mt-task), [RC (tarea)](/visualstudio/msbuild/rc-task), [SetEnv (tarea)](/visualstudio/msbuild/setenv-task), [ VCMessage (tarea)](/visualstudio/msbuild/vcmessage-task), [XDCMake (tarea)](/visualstudio/msbuild/xdcmake-task), [XSD (tarea)](/visualstudio/msbuild/xsd-task).  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild en la línea de comandos  
  
La siguiente instrucción de la [referencia de línea de comandos de MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) muestra que la herramienta msbuild.exe toma un implícita o explícita *project_file* argumento (un archivo .vcxproj para los proyectos de Visual C++) y cero o más de línea de comandos *opciones* argumentos.  
  
> **MSBuild.exe** [ *project_file* ] [ *opciones* ]  
  
Use la **/target** (o **/t**) y **/Property** (o **/p**) opciones de línea de comandos para reemplazar propiedades específicas y destinos Si se especifica en el archivo de proyecto.  
  
Es una función esencial del archivo del proyecto especificar un *destino*, que es una operación determinada que se aplican a su proyecto y las entradas y salidas que son necesarias para realizar esa operación. Un archivo de proyecto puede especificar uno o varios destinos, que pueden incluir un destino predeterminado.  
  
Cada destino consta de una secuencia de uno o varios *tareas*. Cada tarea se representa mediante una clase de .NET Framework que contiene un comando ejecutable. Por ejemplo, el [CL (tarea)](/visualstudio/msbuild/cl-task) contiene el [cl.exe](../build/reference/compiling-a-c-cpp-program.md) comando.  
  
A *parámetro de tarea* es una propiedad de la tarea de clase y normalmente representa una opción de línea de comandos del comando ejecutable. Por ejemplo, el `FavorSizeOrSpeed` parámetro de la `CL` tarea corresponde a la **/Os** y **/Ot** opciones del compilador.  
  
Parámetros de tareas adicionales admiten la infraestructura de MSBuild. Por ejemplo, el `Sources` parámetro de tarea Especifica un conjunto de tareas que se pueden usar en otras tareas. Para obtener más información acerca de las tareas de MSBuild, vea [Task Reference](/visualstudio/msbuild/msbuild-task-reference).  
  
Mayoría de las tareas requiere entradas y salidas, como nombres de archivo y rutas de acceso, cadena, numéricos o booleanos parámetros. Por ejemplo, una entrada habitual es el nombre de un archivo de código fuente .cpp para compilar. Un importante parámetro de entrada es una cadena que especifica la configuración de compilación y la plataforma, por ejemplo, "depurar\|Win32". Entradas y salidas se especifican mediante uno o más XML definido por el usuario `Item` elementos incluidos en un `ItemGroup` elemento.  
  
También puede especificar un archivo de proyecto definida por el usuario *propiedades* y `ItemDefinitionGroup` *elementos*. Propiedades y los elementos forman pares de nombre/valor que se pueden usar como variables en la compilación. El componente de nombre de un par define una *macro*, y el componente de valor declara el *el valor de macro*. Se tiene acceso a una macro de propiedad mediante el uso de $(*nombre*) notación y una macro de elemento se accede mediante %(*nombre*) notación.  
  
Otros elementos XML en un archivo de proyecto pueden probar las macros y, a continuación, condicionalmente establecerá el valor de cualquier macro o controlar la ejecución de la compilación. Nombres de macro y cadenas literales se pueden concatenar para generar estructuras como un ruta de acceso y nombre de archivo. En la línea de comandos, el **/Property** opción establece o invalida una propiedad del proyecto. No se pueden hacer referencia a elementos en la línea de comandos.  
  
El sistema MSBuild puede ejecutar condicionalmente un destino antes o después de otro destino. Además, el sistema puede crear un destino en función de si los archivos que consume el destino son más recientes que los archivos que emite.  
  
## <a name="msbuild-in-the-ide"></a>MSBuild en el IDE  
  
Al establecer propiedades del proyecto en el IDE y, a continuación, guarde el proyecto, Visual C++ escribe los valores de proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto, pero no contiene toda la configuración necesarios para compilar el proyecto. Contiene el archivo de proyecto `Import` elementos que incluyen una red de adicionales *archivos auxiliares.* Los archivos de compatibilidad contienen las restantes propiedades, destinos y valores de configuración necesarios para compilar el proyecto.  
  
La mayoría de los destinos y propiedades en los archivos de compatibilidad existen solamente para implementar el sistema de compilación. La sección siguiente describen algunos destinos y propiedades útiles que puede especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos en los directorios de archivos de soporte técnico.  
  
### <a name="support-file-directories"></a>Directorios de archivos de soporte técnico  
  
De forma predeterminada, los archivos de soporte técnico principales de Visual C++ se encuentran en los directorios siguientes. Los directorios en Microsoft Visual Studio se utilizan en Visual Studio de 2017 y versiones posteriores, cuando se usan los directorios en MSBuild con Visual Studio 2015 y versiones anteriores.  
  
|Directorio|Descripción|  
|---------------|-----------------|  
|*unidad*: \Program archivos *(x86)*\Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\ <br /><br />*unidad*: \Program archivos *(x86)*\MSBuild\Microsoft.Cpp (x86) \v4.0\\*versión*\ |Contiene los archivos de destino principal (.targets) y archivos de propiedades (.props) que se utilizan en los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio.|  
|*unidad*: \Program archivos *(x86)*\Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\ <br /><br />*unidad*: \Program archivos *(x86)*\MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ |Contiene los archivos específicos de la plataforma de destino y la propiedad que invalidan los destinos y propiedades de su directorio primario. Este directorio también contiene un archivo DLL que define las tareas que se utilizan en los destinos de este directorio.<br /><br /> El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio.|  
|*unidad*: \Program archivos *(x86)*\Microsoft Visual Studio\\*año*\\*edición*\Common7\IDE\VC\VCTargets\ Plataformas\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)*\MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\ PlatformToolsets\\*conjunto de herramientas*\ <br /><br />*unidad*: \Program archivos *(x86)*\MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\ |Contiene los directorios que permiten a la compilación generar aplicaciones de Visual C++ utilizando los *conjunto de herramientas*.<br /><br /> El *año* y *edición* 2017 de Visual Studio y ediciones posteriores usan marcadores de posición. El *versión* marcador de posición es V110 para Visual Studio 2012, V120 para Visual Studio 2013 o V140 para Visual Studio 2015. El *plataforma* marcador de posición representa la ARM, Win32 o x64 subdirectorio. El *conjunto de herramientas* marcador de posición representa el subdirectorio del conjunto de herramientas, por ejemplo, v140 para la creación de aplicaciones de Windows mediante el conjunto de herramientas de Visual Studio 2015, v120_xp para compilar para Windows XP con el conjunto de herramientas de Visual Studio 2013 o v110_wp80 a compilar aplicaciones de Windows Phone 8.0 con el conjunto de herramientas de Visual Studio 2012.<br /><br />La ruta de acceso que contiene los directorios que permiten a la compilación generar aplicaciones de Visual C++ 2008 o Visual C++ 2010 no incluye el *versión*y el *plataforma* representa el marcador de posición el procesador Itanium, Win32 o x64 subdirectorio. El *conjunto de herramientas* marcador de posición representa el subdirectorio de conjunto de herramientas v90 o v100.|  
  
### <a name="support-files"></a>Archivos de soporte técnico  
  
Los directorios de archivos de compatibilidad contienen archivos con estas extensiones:  
  
|Extensión|Descripción|  
|---------------|-----------------|  
|.targets|Contiene `Target` elementos XML que especifican las tareas que se ejecutan en el destino. También puede contener `PropertyGroup`, `ItemGroup`, `ItemDefinitionGroup`, definidos por el usuario `Item` elementos que se utilizan para asignar archivos y opciones de línea de comandos a los parámetros de tarea.<br /><br /> Para obtener más información, consulte [elemento Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild).|  
|.props|Contiene `Property Group` definidos por el usuario `Property` elementos XML que especifican los valores de archivo y los parámetros que se usan durante una compilación.<br /><br /> También puede contener `ItemDefinitionGroup` definidos por el usuario `Item` elementos XML que especifican los valores adicionales. Los elementos definidos en un grupo de definición de elemento son similares a propiedades, pero no se pueden tener acceso desde la línea de comandos. Archivos de proyecto de Visual C++, se usa con frecuencia elementos en lugar de propiedades para representar los valores.<br /><br /> Para obtener más información, consulte [elemento ItemGroup (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [elemento ItemDefinitionGroup (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild), y [elemento Item (MSBuild)](/visualstudio/msbuild/item-element-msbuild).|  
|.Xml|Contiene elementos XML que declaran e inicializan los elementos de interfaz de usuario IDE como hojas de propiedades y páginas de propiedades y los controles de cuadro de lista y cuadro de texto.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Sin embargo, los valores de propiedades del IDE se asignan a elementos y las propiedades de compilación.<br /><br /> Mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, archivos de la región de inglés-Estados Unidos están en $(VCTargetsPath) \1033\\.|  
  
## <a name="user-targets-and-properties"></a>Propiedades y destinos de usuario  
  
Para utilizar MSBuild de forma más eficaz en la línea de comandos, es necesario para saber qué propiedades y destinos son útiles y pertinentes. La mayoría de propiedades y destinos ayudan a implementar el sistema de compilación de Visual C++ y, por consiguiente, no son pertinentes para el usuario. En esta sección se describe algunas propiedades orientadas al usuario merece la pena y destinos.  

### <a name="platformtoolset-property"></a>Propiedad PlatformToolset  
  
El `PlatformToolset` propiedad determina qué conjunto de herramientas de Visual C++ se utiliza en la compilación. De forma predeterminada, se utiliza el conjunto de herramientas actual. Cuando se establece esta propiedad, el valor de la propiedad se concatena con cadenas literal para formar la ruta de acceso de un directorio que contiene los archivos de destino y propiedad necesarios para compilar un proyecto para una plataforma concreta. El conjunto de herramientas de plataforma debe estar instalado para compilar con esa versión del conjunto de herramientas de plataforma.  
  
Por ejemplo, establecer el `PlatformToolset` propiedad `v140` usar herramientas de Visual C++ 2015 y bibliotecas para compilar la aplicación:  
  
`msbuild myProject.vcxproj /p:PlatformToolset=v140`  
  
### <a name="preferredtoolarchitecture-property"></a>Propiedad PreferredToolArchitecture  
  
El `PreferredToolArchitecture` propiedad determina si el compilador de 32 bits o 64 bits y herramientas se utilizan en la compilación. Esta propiedad no afecta a la arquitectura de la plataforma de salida o la configuración. De forma predeterminada, MSBuild usa el x86 versión del compilador y herramientas si no se establece esta propiedad.  
  
Por ejemplo, establecer el `PreferredToolArchitecture` propiedad `x64` para usar el compilador de 64 bits y herramientas para compilar la aplicación:  
  
`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>Propiedad UseEnv  
  
De forma predeterminada, la configuración específica de la plataforma para el proyecto actual invalida las variables de entorno PATH, INCLUDE, LIB, LIBPATH, configuración y plataforma. Establecer el `UseEnv` propiedad `true` para garantizar que no se reemplazan las variables de entorno.  
  
`msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>Destinos  
  
Existen cientos de destinos en los archivos de compatibilidad de Visual C++. Sin embargo, la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos de sistema tienen como prefijo un carácter de subrayado (_), o tengan un nombre que comienza con "PrepareFor", "Proceso", "Before", "After", "Pre" o "Post".  
  
En la tabla siguiente se enumera varios destinos útiles orientados al usuario.  
  
|Destino|Descripción|  
|------------|-----------------|  
|BscMake|Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe.|  
|Compilación|Compila el proyecto.<br /><br /> Este es el destino predeterminado para un proyecto.|  
|ClCompile|Ejecuta la herramienta de compilador de Visual C++, cl.exe.|  
|Limpiar|Crear archivos de eliminaciones temporales e intermedias.|  
|Lib|Ejecuta la herramienta Administrador de bibliotecas de Microsoft de 32 bits, lib.exe.|  
|Link|Ejecuta la herramienta del vinculador de Visual C++, link.exe.|  
|ManifestResourceCompile|Extrae una lista de recursos de un manifiesto y, a continuación, ejecuta la herramienta de compilador de recursos de Microsoft Windows, rc.exe.|  
|MIDL|Ejecuta la herramienta de compilador de lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe.|  
|Recompilar|Limpia y, a continuación, compila el proyecto.|  
|ResourceCompile|Ejecuta la herramienta de compilador de recursos de Microsoft Windows, rc.exe.|  
|XdcMake|Ejecuta la herramienta de documentación XML, xdcmake.exe.|  
|XSD|Ejecuta la herramienta de definición de esquemas XML, xsd.exe.|  
  
## <a name="see-also"></a>Vea también  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
