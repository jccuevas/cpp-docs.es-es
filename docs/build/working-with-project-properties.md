---
title: Establece el compilador de C++ y crear propiedades en Visual Studio
description: Usar el IDE de Visual Studio para cambiar las opciones de compilador y vinculador de C++ y otras configuraciones de compilación.
ms.date: 12/10/2018
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 55adb6dc91919bda9c2827a89e5de536667085c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827885"
---
# <a name="set-compiler-and-build-properties"></a>Conjunto de compilador y las propiedades de compilación

En el IDE, toda la información que se necesita para compilar un proyecto se expone como *propiedades*. Esta información incluye el nombre de la aplicación, la extensión (por ejemplo, DLL, LIB, EXE), las opciones del compilador y del vinculador, la configuración del depurador, los pasos de compilación personalizada y muchas otras cosas. Normalmente, se usan las *páginas de propiedades* (**Proyecto &#124; Propiedades**) para ver y modificar estas propiedades. Para obtener acceso a las páginas de propiedades, elija **proyecto > \<nombre del proyecto > propiedades** desde el menú principal o el botón secundario en el nodo del proyecto en **el Explorador de soluciones** y elija **Propiedades**.

## <a name="default-properties"></a>Propiedades predeterminadas

Al crear un proyecto, el sistema asigna valores a varias propiedades. Los valores predeterminados varían ligeramente según el tipo de proyecto y las opciones que se elijan en el Asistente para aplicaciones. Por ejemplo, un proyecto de ATL tiene propiedades relacionadas con los archivos MIDL, pero estas no están presentes en una aplicación de consola básica. Las propiedades predeterminadas se muestran en el panel General de las páginas de propiedades:

![Valores predeterminados del proyecto de Visual C&#43;&#43;](media/visual-c---project-defaults.png "Visual C++ Project Defaults")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Aplicación de propiedades para compilar las configuraciones y plataformas de destino

Algunas propiedades, como el nombre de la aplicación, se aplican a todas las variaciones de compilación, independientemente de la plataforma de destino o si es una compilación de depuración o versión. Pero la mayoría de las propiedades dependen de la configuración. Esto se debe a que el compilador tiene que saber en qué plataforma concreta se va a ejecutar el programa y qué opciones específicas del compilador se van a usar para generar el código correcto. Por tanto, cuando se establece una propiedad, es importante prestar atención a la configuración y plataforma a las que se debe aplicar el valor nuevo. ¿Se debe aplicar solo a las compilaciones Debug Win32 o también a Debug ARM y Debug x64? Por ejemplo, la propiedad **Optimización** se establece de forma predeterminada en **Maximizar velocidad (/O2)** en una configuración de versión, pero está deshabilitada en la configuración de depuración.

Las páginas de propiedades están diseñadas para que siempre se pueda ver y, si es necesario modificar, la configuración y la plataforma a las que se debe aplicar un valor de propiedad. En la ilustración siguiente se muestran las páginas de propiedades con la información de la plataforma y la configuración en los cuadros de lista de la parte superior. Cuando aquí se establece la propiedad **Optimización**, solo se aplica a las compilaciones Debug Win32, que es la configuración activa, como se muestra mediante las flechas de color rojo.

![Páginas de propiedades de Visual C&#43;&#43; en las que se muestra la configuración activa](media/visual-c---property-pages-showing-active-configuration.png "Visual C++ Property Pages showing active configuration")

En la ilustración siguiente se muestra la misma página de propiedades de proyecto, pero la configuración se ha cambiado a Release. Observe el valor diferente para la propiedad Optimización. Observe también que la configuración activa sigue siendo Debug. Aquí se pueden establecer propiedades para cualquier configuración; no tiene que ser la activa.

![Páginas de propiedades de Visual C&#43;&#43; en las que se muestra la configuración de versión](media/visual-c---property-pages-showing-release-config.png "Visual C++ Property Pages showing release config")

## <a name="target-platforms"></a>Plataformas de destino

*Plataforma de destino* hace referencia al tipo de dispositivo o sistema operativo en que se va a ejecutar el archivo ejecutable. Un proyecto se puede compilar para más de una plataforma. Las plataformas de destino disponibles para los proyectos de C++ dependen del tipo de proyecto; se incluyen, pero no se limitan a Win32, x64, ARM, iOS y Android.     La plataforma de destino **x86** que es posible que vea en el **Administrador de configuración** es idéntica a **Win32** en los proyectos nativos de C++. Win32 significa Windows de 32 bits y **x64** significa Windows de 64 bits. Para obtener más información sobre estas dos plataformas, vea [Running 32-bit applications](/windows/desktop/WinProg64/running-32-bit-applications) (Ejecución de aplicaciones de 32 bits).

El valor de plataforma de destino **Cualquier CPU** que es posible que vea en el **Administrador de configuración** no tiene ningún efecto en los proyectos nativos de C++; es relevante para proyectos de C++/CLI y otros tipos de proyecto de .NET. Para obtener más información, consulte [/CLRIMAGETYPE (especificar tipo de imagen de CLR)](reference/clrimagetype-specify-type-of-clr-image.md).


Para obtener más información acerca de cómo establecer las propiedades de una compilación de depuración, vea:

- [Configuración del proyecto para una configuración de depuración de C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Configuración y preparación de la depuración](/visualstudio/debugger/debugger-settings-and-preparation)
- [Preparación de la depuración: Tipos de proyecto de Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Definición de archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Opciones del compilador y vinculador de C++

Opciones del compilador y vinculador de C++ se encuentran en el **C o C++** y **vinculador** nodos en el panel izquierdo bajo **propiedades de configuración**. Estos se traducen directamente a las opciones de línea de comandos que se pasarán al compilador. Para leer la documentación acerca de una opción específica, seleccione la opción en el panel central y presione **F1**. O bien, puede examinar la documentación para todas las opciones en [opciones del compilador MSVC](reference/compiler-options.md) y [las opciones del vinculador MSVC](reference/linker-options.md). 

El **páginas de propiedades** cuadro de diálogo muestra solo las páginas de propiedades que son relevantes para el proyecto actual. Por ejemplo, si el proyecto no tiene un archivo .idl, la página de propiedades de MIDL no se muestra. Para obtener más información acerca de la configuración en cada página de propiedades, vea [Property Pages (C++)](reference/property-pages-visual-cpp.md). 

## <a name="directory-and-path-values"></a>Valores de directorio y la ruta de acceso

MSBuild admite el uso de constantes de tiempo de compilación denominado "macros" para ciertos valores de cadena que incluyen los directorios y rutas de acceso. Estos se exponen en las páginas de propiedades, donde puede hacer referencia a y modificarlos usando la [Editor de propiedades](#property_editor). 

La ilustración siguiente muestra las páginas de propiedades de un proyecto de Visual C++. En el panel de la izquierda, está seleccionada la **regla** *Directorios VC++* y en el de la derecha se muestran las propiedades asociadas a esa regla. El `$(...)` se denominan valores *macros*. Una *macro* es una constante de tiempo de compilación que puede hacer referencia a un valor que se define por Visual Studio o el sistema MSBuild, o un valor definido por el usuario. Mediante el uso de macros en lugar de valores codificados de forma rígida, como las rutas de acceso de directorio, resultará más fácil compartir valores de propiedad entre equipos y entre las versiones de Visual Studio y podrá asegurarse de que la configuración del proyecto participa correctamente en [ herencia de propiedad](project-property-inheritance.md). 

![Páginas de propiedades del proyecto](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Se puede usar el Editor de propiedades para ver los valores de todas las macros disponibles. (Las macros se describen en la sección [Macros de la página de propiedades](#bkmkPropertiesVersusMacros) más adelante en este artículo).

### <a name="predefined-macros"></a>Macros predefinidas

*macros globales*<br/>
Se aplica a todos los elementos de una configuración de proyecto. Tiene la sintaxis `$(name)`. Un ejemplo de una macro global es `$(VCInstallDir)`, que almacena el directorio raíz de la instalación de Visual Studio. Una macro global corresponde a `PropertyGroup` en MSBuild.

*macros de elemento*<br/>
Tiene la sintaxis `%(name)`. Para un archivo, una macro de elemento solo se aplica a ese archivo; por ejemplo, puede utilizar `%(AdditionalIncludeDirectories)` para especificar directorios de inclusión que solo se aplican a un archivo determinado. Esta clase de macro de elemento corresponde a metadatos `ItemGroup` en MSBuild. Cuando se utiliza en el contexto de una configuración de proyecto, se aplica una macro de elemento a todos los archivos de un tipo determinado. Por ejemplo, la propiedad de configuración **Definiciones de preprocesador** de C/C++ puede tomar una macro de elemento `%(PreprocessorDefinitions)` que se aplica a todos los archivos .cpp del proyecto. Esta clase de macro de elemento corresponde a metadatos `ItemDefinitionGroup` en MSBuild. Para obtener más información, consulte [Definiciones de elementos](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Macros definidas por el usuario

Se pueden crear *macros definidas por el usuario* para usarlas como variables en compilaciones de proyectos. Por ejemplo, puede crear una macro definida por el usuario que proporcione un valor a un paso de compilación personalizada o a una herramienta de compilación personalizada. Una macro definida por el usuario es un par de nombre y valor. En un archivo de proyecto, use la notación **$(**<em>nombre</em>**)** para acceder al valor.

La macro definida por el usuario se almacena en una hoja de propiedades. Si el proyecto no contuviera una hoja de propiedades, puede crear uno siguiendo los pasos descritos en [configuraciones de proyecto de Visual Studio C++ del recurso compartido o resuse](#bkmkPropertySheets).

#### <a name="to-create-a-user-defined-macro"></a>Para crear una macro definida por el usuario

1. En la ventana **Administrador de propiedades** (en la barra de menús, seleccione **Ver**, **Administrador de propiedades**), abra el menú contextual de una hoja de propiedades (su nombre termina en .user) y después seleccione Propiedades. Se abre el cuadro de diálogo **Páginas de propiedades** de esa hoja de propiedades.

1. En el panel de la izquierda del cuadro de diálogo, seleccione **Macros de usuario**. En el panel de la derecha, haga clic en el botón **Agregar macro** para abrir el cuadro de diálogo **Agregar macro de usuario**.

1. En el cuadro de diálogo, especifique un nombre y un valor para la macro. Opcionalmente, active la casilla **Establecer esta macro como variable de entorno en el entorno de compilación**.

## <a name="property_editor">Editor de propiedades</a>

Puede utilizar el editor de propiedades para modificar determinadas propiedades de cadena y seleccionar macros como valores. Para tener acceso al editor de propiedades, seleccione una propiedad en una página de propiedades y elija el botón de flecha abajo de la derecha. Si la lista desplegable contiene **\<Editar>**, podrá decidir si quiere que muestre el Editor de propiedades para esa propiedad.

![Menú desplegable&#95;Editor&#95;de propiedades](media/property_editor_dropdown.png "Property_Editor_Dropdown")

En el Editor de propiedades, puede hacer clic en el botón **Macros** para ver las macros disponibles y sus valores actuales. En la ilustración siguiente se muestra el Editor de propiedades para la propiedad **Directorios de inclusión adicionales** después de haber hecho clic en el botón **Macros**. Cuando se activa la casilla **Heredar de primario o valores pred. del proyecto** y se agrega un valor nuevo, se anexa a cualquier valor que se está heredando actualmente. Si desactiva la casilla, el nuevo valor reemplaza los valores heredados. En la mayoría de los casos, deje la casilla activada.

![Editor de propiedades, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Agregar un directorio de inclusión al conjunto de directorios predeterminados

Cuando agrega un directorio de inclusión a un proyecto, es importante no invalidar todos los directorios predeterminados. La forma correcta de agregar un directorio es anexar la ruta de acceso nueva, por ejemplo "C:\MyNewIncludeDir\", y luego anexar la macro **$(IncludePath)** al valor de propiedad.

## <a name="quickly-browse-and-search-all-properties"></a>Examinar y buscar todas las propiedades rápidamente

La página de propiedades **Todas las opciones** (bajo el nodo **Propiedades de configuración &#124; C/C++** del cuadro de diálogo **Páginas de propiedades**) proporciona una forma rápida de examinar y buscar las propiedades disponibles en el contexto actual. Tiene un cuadro de búsqueda especial y una sintaxis simple para ayudarle a filtrar los resultados:

Ningún prefijo:<br/>
Busque solo en los nombres de propiedad (subcadena sin distinción entre mayúsculas y minúsculas).

'/' o bien '-':<br/>
Buscar solo en modificadores de compilador (prefijo sin distinción entre mayúsculas y minúsculas)

v:<br/>
Busque solo en los valores (subcadena sin distinción entre mayúsculas y minúsculas).

## <a name="set-environment-variables-for-a-build"></a>Establecer variables de entorno para una compilación

El compilador de MSVC (cl.exe) reconoce determinadas variables de entorno, en concreto LIB, LIBPATH, PATH e INCLUDE. Al compilar con el IDE, las propiedades establecidas en la página de propiedades [Directorios de VC++](reference/vcpp-directories-property-page.md) se usan para establecer esas variables de entorno. Si los valores LIB, LIBPATH e INCLUDE se han definido, por ejemplo mediante el símbolo del sistema del desarrollador, estos se reemplazarán por los valores de las propiedades de MSBuild correspondientes. La compilación luego antepone el valor de la propiedad de directorios ejecutable de los directorios VC++ en PATH. Puede establecer una variable de entorno definida por el usuario si crea una macro definida por el usuario y activa la casilla **Establecer esta macro como variable de entorno en el entorno de compilación**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Establecer variables de entorno para una sesión de depuración

En el panel de la izquierda del cuadro de diálogo **Páginas de propiedades** del proyecto, expanda **Propiedades de configuración** y, después, seleccione **Depuración**.

En el panel de la derecha, modifique las opciones **Entorno** o **Combinar entorno**, y después haga clic en el botón **Aceptar**.

## <a name="in-this-section"></a>En esta sección

[Recurso compartido o resuse configuración del proyecto de Visual Studio](create-reusable-property-configurations.md)<br/>
Cómo crear un archivo .props configuraciones de compilación personalizadas que se pueden compartir o resused.

[Herencia de propiedades de proyecto](project-property-inheritance.md)<br/>
Describe el orden de evaluación de los archivos .props, .targets, .vcxproj archivos y variables de entorno del proceso de compilación.

[Modificar las propiedades y destinos sin necesidad de cambiar el archivo de proyecto](modify-project-properties-without-changing-project-file.md)<br/>
Cómo crear una configuración de compilación temporal sin tener que modificar un archivo de proyecto. 

## <a name="see-also"></a>Vea también

[Proyectos de Visual Studio - C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Estructura de archivo .vcxproj y .props](reference/vcxproj-file-structure.md)<br/>
[Archivos XML de página de propiedades](reference/property-page-xml-files.md)<br/>