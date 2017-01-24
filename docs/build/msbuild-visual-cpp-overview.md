---
title: "Informaci&#243;n general sobre MSBuild (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Información general sobre MSBuild"
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Informaci&#243;n general sobre MSBuild (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MSBuild es el estándar de sistema de compilación para proyectos de Visual C++. Cuando compila un proyecto en el entorno de desarrollo integrado (IDE) de Visual Studio, utiliza la herramienta msbuild.exe, un archivo de proyecto basado en XML y archivos de configuración opcionales. Aunque puede utilizar msbuild.exe y un archivo de proyecto en la línea de comandos, el IDE proporciona una interfaz de usuario para que pueda configurar y compilar un proyecto más fácilmente. Esta información general describe cómo Visual C++ utiliza el sistema MSBuild.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Lea los siguientes documentos sobre MSBuild.  
  
 [MSBuild](MSBuild1.md)  
 Información general de conceptos de MSBuild.  
  
 [Referencia de MSBuild](../Topic/MSBuild%20Reference.md)  
 Información de referencia sobre el sistema MSBuild.  
  
 [Referencia de esquema de archivo de proyecto](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)  
 Enumera los elementos de esquema XML de MSBuild, junto con sus atributos y elementos primarios y secundarios. Observe especialmente la [ItemGroup](../Topic/ItemGroup%20Element%20\(MSBuild\).md), [PropertyGroup](../Topic/PropertyGroup%20Element%20\(MSBuild\).md), [destino](../Topic/Target%20Element%20\(MSBuild\).md), y [tarea](../Topic/Task%20Element%20\(MSBuild\).md) elementos.  
  
 [Referencia de línea de comandos](../Topic/MSBuild%20Command-Line%20Reference.md)  
 Describe los argumentos de línea de comandos y opciones que puede usar con msbuild.exe.  
  
 [Referencia de tareas](../Topic/MSBuild%20Task%20Reference.md)  
 Describe las tareas de MSBuild. Tenga en cuenta especialmente estas tareas, que son específicas de Visual C++: [tarea BscMake](../Topic/BscMake%20Task.md), [CL (tarea)](../Topic/CL%20Task.md), [CPPClean (tarea)](../Topic/CPPClean%20Task.md), [LIB (tarea)](../Topic/LIB%20Task.md), [Vincular tarea](../Topic/Link%20Task.md), [MIDL (tarea)](../Topic/MIDL%20Task.md), [MT (tarea)](../Topic/MT%20Task.md), [RC (tarea)](../Topic/RC%20Task.md), [SetEnv (tarea)](../Topic/SetEnv%20Task.md), [VCMessage (tarea)](../Topic/VCMessage%20Task.md), [XDCMake (tarea)](../Topic/XDCMake%20Task.md), [XSD (tarea)](../Topic/XSD%20Task.md).  
  
## <a name="msbuild-on-the-command-line"></a>MSBuild en la línea de comandos  
 La siguiente instrucción de la [referencia de línea de comandos](../Topic/MSBuild%20Command-Line%20Reference.md) documento muestra que la herramienta msbuild.exe toma un implícita o explícita `project file` argumento (un archivo .vcxproj para los proyectos de Visual C++) y cero o más de línea de comandos `options`.  
  
 **msbuild.exe [** `project file` **] [** `options` **]**  
  
 Utilice el **/target** (o **/t**) y **/Property** (o **/p**) las opciones de línea de comandos para invalidar las propiedades y los destinos que se especifican en el archivo de proyecto.  
  
 Una función esencial del archivo de proyecto es especificar un *destino*, que es una operación determinada que se aplican a su proyecto y las entradas y salidas que son necesarias para realizar esa operación. Un archivo de proyecto puede especificar uno o varios destinos, que pueden incluir un destino predeterminado.  
  
 Cada destino consta de una secuencia de uno o más *tareas*. Cada tarea se representa mediante una clase de .NET Framework que contiene un comando ejecutable. Por ejemplo, la [tarea CL](../Topic/CL%20Task.md) contiene el [cl.exe](../build/reference/compiling-a-c-cpp-program.md) comando.  
  
 Un *parámetro de tarea* es una propiedad de la tarea de clase y que normalmente representa una opción de línea de comandos del comando ejecutable. Por ejemplo, el `FavorSizeOrSpeed` parámetro de la `CL` tarea corresponde a la **/Os** y **/Ot** Opciones del compilador.  
  
 Parámetros de tareas adicionales admiten la infraestructura de MSBuild. Por ejemplo, el `Sources` parámetro de tarea Especifica un conjunto de tareas que pueden ser utilizados por otras tareas. Para obtener más información acerca de las tareas de MSBuild, consulte [Task Reference](../Topic/MSBuild%20Task%20Reference.md).  
  
 La mayoría de las tareas requieren entradas y salidas, como nombres de archivo, rutas de acceso de cadena, numéricos o booleanos parámetros. Por ejemplo, una entrada habitual es el nombre de un archivo de código fuente .cpp para compilar. Un parámetro de entrada importante es una cadena que especifica la configuración de compilación y plataforma, por ejemplo, "depuración &#124; Win32 ". Entradas y salidas se especifican uno o más XML definido por el usuario `Item` elementos incluidos en un `ItemGroup` elemento.  
  
 También puede especificar un archivo de proyecto definida por el usuario *propiedades* y *grupo de definiciones de elemento**elementos*. Propiedades y elementos forman pares de nombre/valor que se pueden usar como variables en la compilación. El componente de nombre de un par define una *macro*, y el componente de valor declara el *el valor de macro*. Una macro de propiedad se accede mediante $(*nombre*) notación y una macro de elemento se accede mediante %(*nombre*) notación.  
  
 Otros elementos XML de un archivo de proyecto pueden probar las macros y, a continuación, condicionalmente establecer el valor de una macro o controlar la ejecución de la compilación. Nombres de macro y las cadenas literales se pueden concatenar para generar estructuras como un ruta de acceso y nombre de archivo. En la línea de comandos, el **/Property** opción establece o invalida una propiedad de proyecto. No se pueden hacer referencia a elementos en la línea de comandos.  
  
 El sistema MSBuild puede ejecutar condicionalmente un destino antes o después de otro destino. Además, el sistema puede compilar un destino basándose en si los archivos que usa el destino son más recientes que los archivos que emite.  
  
## <a name="msbuild-in-the-ide"></a>MSBuild en el IDE  
 Al establecer las propiedades del proyecto en el IDE y, a continuación, guarde el proyecto, Visual C++ escribe la configuración del proyecto en el archivo de proyecto. El archivo de proyecto contiene valores que son únicos para el proyecto, pero no contiene todas las configuraciones necesarias para compilar el proyecto. El archivo de proyecto contiene `Import` elementos que incluyen una red de adicionales *archivos auxiliares.* Los archivos de compatibilidad contienen las restantes propiedades, destinos y valores de configuración necesarios para compilar el proyecto.  
  
 La mayoría de los destinos y propiedades de los archivos de compatibilidad existen solamente para implementar el sistema de compilación. La siguiente sección describen algunos destinos y propiedades útiles que puede especificar en la línea de comandos de MSBuild. Para conocer más destinos y propiedades, explore los archivos en los directorios de archivos de soporte técnico.  
  
### <a name="support-file-directories"></a>Directorios de archivos de soporte técnico  
 De forma predeterminada, los archivos de soporte técnico principales de Visual C++ se encuentran en los directorios siguientes.  
  
|Directorio|Descripción|  
|---------------|-----------------|  
|*unidad*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*versión*\|Contiene los archivos de destino principal (.targets) y archivos de propiedad (.props) que se utilizan en los destinos. De forma predeterminada, la macro $(VCTargetsPath) hace referencia a este directorio.|  
|*unidad*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\|Contiene los archivos específicos de la plataforma de destino y propiedad que invalidan los destinos y propiedades de su directorio primario. Este directorio también contiene un archivo .dll que define las tareas que se utilizan en los destinos de este directorio.<br /><br /> El *plataforma* marcador de posición representa el `ARM`, `Win32`, o `x64` subdirectorio.|  
|*unidad*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\\*versión*\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\|Contiene los directorios que permiten generar aplicaciones de Visual C++ con los valores especificados en la compilación *versión* del conjunto de herramientas.<br /><br /> El *plataforma* marcador de posición representa el `ARM`, `Win32`, o `x64` subdirectorio. El *toolset* marcador de posición representa el subdirectorio del conjunto de herramientas para crear aplicaciones de Windows, Windows XP o Windows Phone.|  
|*unidad*: \Program Files\MSBuild\Microsoft.Cpp\v4.0\Platforms\\*plataforma*\PlatformToolsets\\*conjunto de herramientas*\|Contiene los directorios que permiten la compilación generar 9.0 o aplicaciones de Visual C++ 10.0.<br /><br /> El *plataforma* marcador de posición representa el `Itanium`, `Win32`, o `x64` subdirectorio. El *toolset* marcador de posición representa el `v90` o `v100` subdirectorio del conjunto de herramientas.|  
  
### <a name="support-files"></a>Archivos de soporte técnico  
 Los directorios de archivos de compatibilidad contienen archivos con las siguientes extensiones.  
  
|Extensión|Descripción|  
|---------------|-----------------|  
|.targets|Contiene `Target` elementos XML que especifican las tareas que se ejecutan en el destino. También puede contener `Property Group`, `Item Group`, `Item Definition Group`, definidos por el usuario `Item` elementos que se utilizan para asignar archivos y opciones de línea de comandos a los parámetros de tarea.<br /><br /> Para obtener más información, consulte [elemento Target (MSBuild)](../Topic/Target%20Element%20\(MSBuild\).md).|  
|.props|Contiene `Property Group` definidos por el usuario `Property` elementos XML que especifican los valores de parámetro y de archivo que se usan durante una compilación.<br /><br /> También puede contener `Item Definition Group` definidos por el usuario `Item` elementos XML que especifican opciones de configuración adicionales. Los elementos definidos en un grupo de definiciones de elemento son similares a las propiedades, pero no pueden obtenerse acceso desde la línea de comandos. Archivos de proyecto de Visual C++, se utiliza con frecuencia elementos en lugar de propiedades para representar los valores.<br /><br /> Para obtener más información, consulte [elemento ItemGroup (MSBuild)](../Topic/ItemGroup%20Element%20\(MSBuild\).md), [elemento ItemDefinitionGroup (MSBuild)](../Topic/ItemDefinitionGroup%20Element%20\(MSBuild\).md), y [elemento Item (MSBuild)](../Topic/Item%20Element%20\(MSBuild\).md).|  
|.xml|Contiene elementos XML que declaran e inicializan elementos de interfaz de usuario IDE como hojas de propiedades y páginas de propiedades y los controles de cuadro de lista y cuadro de texto.<br /><br /> Los archivos .xml admiten directamente el IDE, no MSBuild. Sin embargo, los valores de propiedades IDE se asignan a elementos y las propiedades de compilación.<br /><br /> Mayoría de los archivos .xml se encuentran en un subdirectorio específico de la configuración regional. Por ejemplo, archivos para la región de inglés-Estados Unidos se encuentran en $(VCTargetsPath) \1033\\.|  
  
## <a name="user-targets-and-properties"></a>Propiedades y destinos de usuario  
 Para utilizar MSBuild más eficazmente en la línea de comandos, resulta útil para saber qué propiedades y destinos son útiles y pertinentes. La mayoría de propiedades y destinos ayudan a implementar el sistema de compilación de Visual C++ y, por consiguiente, no son relevantes para el usuario. Esta sección describen algunos objetivos y merece la pena propiedades orientadas al usuario.  
  
### <a name="platformtoolset-property"></a>Propiedad PlatformToolset  
 El `PlatformToolset` propiedad determina qué conjunto de herramientas de Visual C++ se utiliza en la compilación. El valor de la propiedad se concatena con cadenas literal para formar la ruta de acceso de un directorio que contiene los archivos de destino y propiedad necesarios para compilar un proyecto para una plataforma determinada.  
  
 Establecer el `PlatformToolset` propiedad `v110` usar [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] Herramientas y bibliotecas para compilar la aplicación.  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v110`  
  
 Establecer el `PlatformToolset` propiedad `v100` usar [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] Herramientas y bibliotecas para compilar la aplicación.  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v100`  
  
 Establecer el `PlatformToolset` propiedad `v90` utilizar bibliotecas y herramientas de Visual C++ 2008 para compilar la aplicación. El conjunto de herramientas de Visual C++ 2008 ya debe instalarse en el equipo para que esta propiedad sea eficaz.  
  
 `msbuild myProject.vcxproj /p:PlatformToolset=v90`  
  
### <a name="preferredtoolarchitecture-property"></a>Propiedad PreferredToolArchitecture  
 El `PreferredToolArchitecture` propiedad determina si el compilador de 32 bits o 64 bits y herramientas se utilizan en la compilación. Esta propiedad no afecta a la arquitectura de la plataforma de salida o la configuración. De forma predeterminada, MSBuild utiliza la x86 versión del compilador y herramientas si esta propiedad no está establecida o está establecido en cualquier valor distinto de `x64`.  
  
 Establecer el `PreferredToolArchitecture` propiedad `x64` utilizar el compilador de 64 bits y herramientas para compilar la aplicación.  
  
 `msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="useenv-property"></a>Propiedad UseEnv  
 De forma predeterminada, la configuración específica de la plataforma para el proyecto actual reemplazar las variables de entorno PATH, INCLUDE, LIB, LIBPATH, CONFIGURACIÓN y PLATAFORMA. Establecer el `UseEnv` propiedad `true` para garantizar que no se reemplazarán las variables de entorno.  
  
 `msbuild myProject.vcxproj /p:UseEnv=true`  
  
### <a name="targets"></a>Destinos  
 Existen centenares de destinos en los archivos de compatibilidad de Visual C++. Sin embargo, la mayoría son destinos orientados al sistema que el usuario puede omitir. La mayoría de los destinos de sistema están precedidos por un carácter de subrayado (_) o tienen un nombre que comienza con "PrepareFor", "Compute", "Before", "After", "Pre" o "Post".  
  
 La siguiente tabla enumera varios destinos merece la pena orientados al usuario.  
  
|Destino|Descripción|  
|------------|-----------------|  
|BscMake|Ejecuta la herramienta Utilidad de mantenimiento de información de examen de Microsoft, bscmake.exe.|  
|Compilación|Compila el proyecto.<br /><br /> Este es el destino predeterminado para un proyecto.|  
|ClCompile|Ejecuta la herramienta de compilador de Visual C++, cl.exe.|  
|Limpiar|Crear archivos de eliminaciones temporales e intermedias.|  
|Lib|Ejecuta la herramienta Administrador de bibliotecas de Microsoft de 32 bits, lib.exe.|  
|Link|Ejecuta la herramienta de vinculador de Visual C++, link.exe.|  
|ManifestResourceCompile|Extrae una lista de recursos de un manifiesto y, a continuación, ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|  
|MIDL|Ejecuta la herramienta de compilador de lenguaje de definición de interfaz de Microsoft (MIDL), midl.exe.|  
|Recompilar|Limpia y, a continuación, compila el proyecto.|  
|ResourceCompile|Ejecuta la herramienta compilador de recursos de Microsoft Windows, rc.exe.|  
|XdcMake|Ejecuta la herramienta de documentación XML, xdcmake.exe.|  
|XSD|Ejecuta la herramienta de definición de esquemas XML, xsd.exe.|  
  
## <a name="see-also"></a>Vea también  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)