---
title: Trabajar con propiedades de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4420bdac9e788f80142546d8b09781a8aa3ce06d
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821392"
---
# <a name="working-with-project-properties"></a>Trabajar con configuraciones de proyecto

En el IDE, toda la información que se necesita para compilar un proyecto se expone como *propiedades*. Esta información incluye el nombre de la aplicación, la extensión (por ejemplo, DLL, LIB, EXE), las opciones del compilador y del vinculador, la configuración del depurador, los pasos de compilación personalizada y muchas otras cosas. Normalmente, se usan las *páginas de propiedades* (**Proyecto &#124; Propiedades**) para ver y modificar estas propiedades.

Al crear un proyecto, el sistema asigna valores a varias propiedades. Los valores predeterminados varían ligeramente según el tipo de proyecto y las opciones que se elijan en el Asistente para aplicaciones. Por ejemplo, un proyecto de ATL tiene propiedades relacionadas con los archivos MIDL, pero estas no están presentes en una aplicación de consola básica. Las propiedades predeterminadas se muestran en el panel General de las páginas de propiedades:

![Valores predeterminados del proyecto de Visual C&#43;&#43;](../ide/media/visual-c---project-defaults.png "Visual C++ Project Defaults")

Algunas propiedades, como el nombre de la aplicación, se aplican a todas las variaciones de compilación, independientemente de la plataforma de destino o si es una compilación de depuración o versión. Pero la mayoría de las propiedades dependen de la configuración. Esto se debe a que el compilador tiene que saber en qué plataforma concreta se va a ejecutar el programa y qué opciones específicas del compilador se van a usar para generar el código correcto. Por tanto, cuando se establece una propiedad, es importante prestar atención a la configuración y plataforma a las que se debe aplicar el valor nuevo. ¿Se debe aplicar solo a las compilaciones Debug Win32 o también a Debug ARM y Debug x64? Por ejemplo, la propiedad **Optimización** se establece de forma predeterminada en **Maximizar velocidad (/O2)** en una configuración de versión, pero está deshabilitada en la configuración de depuración.

Las páginas de propiedades están diseñadas para que siempre se pueda ver y, si es necesario modificar, la configuración y la plataforma a las que se debe aplicar un valor de propiedad. En la ilustración siguiente se muestran las páginas de propiedades con la información de la plataforma y la configuración en los cuadros de lista de la parte superior. Cuando aquí se establece la propiedad **Optimización**, solo se aplica a las compilaciones Debug Win32, que es la configuración activa, como se muestra mediante las flechas de color rojo.

![Páginas de propiedades de Visual C&#43;&#43; en las que se muestra la configuración activa](../ide/media/visual-c---property-pages-showing-active-configuration.png "Visual C++ Property Pages showing active configuration")

En la ilustración siguiente se muestra la misma página de propiedades de proyecto, pero la configuración se ha cambiado a Release. Observe el valor diferente para la propiedad Optimización. Observe también que la configuración activa sigue siendo Debug. Aquí se pueden establecer propiedades para cualquier configuración; no tiene que ser la activa.

![Páginas de propiedades de Visual C&#43;&#43; en las que se muestra la configuración de versión](../ide/media/visual-c---property-pages-showing-release-config.png "Visual C++ Property Pages showing release config")

El propio sistema de proyectos se basa en MSBuild, que define los formatos de archivo y las reglas para compilar proyectos de cualquier tipo. MSBuild administra gran parte de la complejidad de la compilación para varias plataformas y configuraciones, pero debe comprender un poco su funcionamiento. Esto es especialmente importante si quiere definir configuraciones personalizadas o crear conjuntos reutilizables de propiedades que pueda compartir e importar en varios proyectos.

Las propiedades del proyecto se almacenan directamente en el archivo de proyecto (*.vcxproj) o en otros archivos .xml o .props que el archivo de proyecto importa y que proporcionan los valores predeterminados. Como se mostró anteriormente, se puede asignar otro valor a la misma propiedad para la misma configuración en otros archivos. Cuando se compila un proyecto, el motor de MSBuild evalúa el archivo de proyecto y todos los archivos importados en un orden bien definido (descrito a continuación). Al evaluar cada archivo, los valores de propiedad definidos en ese archivo invalidarán los valores existentes. Los valores que no se especifiquen se heredan de los archivos que se evaluaron anteriormente. Por tanto, cuando se establece una propiedad con las páginas de propiedades, también es importante prestar atención a dónde se establece. Si se establece una propiedad en "X" en un archivo .props, pero se establece en "Y" en el archivo de proyecto, el proyecto se compilará con la propiedad establecida en "Y". Si la misma propiedad se establece en "Z" en un elemento de proyecto, como un archivo .cpp, el motor de MSBuild usará el valor de "Z". Para obtener más información, vea [Herencia de propiedades](#bkmkPropertyInheritance) más adelante en este artículo.

## <a name="build-configurations"></a>Configuraciones de compilación

Una configuración es solo un grupo arbitrario de propiedades a las que se asigna un nombre. Visual Studio proporciona configuraciones de depuración y versión, y cada una establece varias propiedades de forma adecuada para una compilación de depuración o de versión. Se puede usar el **Administrador de configuración** para definir configuraciones personalizadas como una manera cómoda de agrupar propiedades para un tipo de compilación específico. El Administrador de propiedades se usa para operaciones avanzadas con las propiedades, pero se presenta aquí porque ayuda a visualizar las configuraciones de propiedades. Se puede acceder a él desde **Ver &#124; Administrador de propiedades** o **Ver &#124; Otras ventanas &#124; Administrador de propiedades** según la configuración. Tiene nodos para cada par de configuración y plataforma del proyecto. En cada uno de estos nodos hay nodos para las hojas de propiedades (los archivos .props) que establecen algunas propiedades específicas para esa configuración.

![Administrador de propiedades](../ide/media/property-manager.png "Property Manager")

Si va al panel General en las páginas de propiedades (vea la ilustración anterior) y establece la propiedad Juego de caracteres en "Sin establecer" en lugar de "Usar Unicode" y hace clic en **Aceptar**, en el Administrador de propiedades no se mostrará ninguna hoja de propiedades **Compatibilidad con Unicode** para la configuración actual, pero seguirá estando ahí para otras configuraciones.

Para obtener más información sobre el Administrador de propiedades y las hojas de propiedades, vea [Crear configuraciones de propiedad reutilizables](#bkmkPropertySheets) más adelante en este artículo.

> [!TIP]
> El archivo .user es una característica heredada y se recomienda eliminarlo para conservar las propiedades agrupadas de forma correcta según la configuración y la plataforma.

## <a name="target-platforms"></a>Plataformas de destino

*Plataforma de destino* hace referencia al tipo de dispositivo o sistema operativo en que se va a ejecutar el archivo ejecutable. Un proyecto se puede compilar para más de una plataforma. Las plataformas de destino disponibles para los proyectos de C++ dependen del tipo de proyecto; se incluyen, pero no se limitan a Win32, x64, ARM, iOS y Android.     La plataforma de destino **x86** que es posible que vea en el **Administrador de configuración** es idéntica a **Win32** en los proyectos nativos de C++. Win32 significa Windows de 32 bits y **x64** significa Windows de 64 bits. Para obtener más información sobre estas dos plataformas, vea [Running 32-bit applications](/windows/desktop/WinProg64/running-32-bit-applications) (Ejecución de aplicaciones de 32 bits).

El valor de plataforma de destino **Cualquier CPU** que es posible que vea en el **Administrador de configuración** no tiene ningún efecto en los proyectos nativos de C++; es relevante para proyectos de C++/CLI y otros tipos de proyecto de .NET. Para obtener más información, consulte [/CLRIMAGETYPE (especificar tipo de imagen de CLR)](../build/reference/clrimagetype-specify-type-of-clr-image.md).

## <a name="property-pages"></a>páginas de propiedades

Como se mencionó anteriormente, el sistema de proyectos de Visual C++ se basa en [MSBuild](/visualstudio/msbuild/msbuild-properties) y los valores se almacenan en el archivo de proyecto XML, los archivos .props y .targets predeterminados. Para Visual Studio 2015, estos archivos se encuentran en **\Archivos de programa (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Para Visual Studio 2017, estos archivos se encuentran en **\\Archivos de programa (x86)\\Microsoft Visual Studio\\2017\\_edición_\\Common7\\IDE\\VC\\VCTargets**, donde _edición_ es la edición de Visual Studio instalada. Las propiedades también se almacenan en los archivos .props personalizados que es posible que se agreguen a un proyecto propio. Se recomienda encarecidamente NO modificar esos archivos de forma manual y, en su lugar, usar las páginas de propiedades del IDE para modificar todas las propiedades, en especial las que participan en la herencia, a menos que se tenga un conocimiento excelente de MSBuild.

La ilustración siguiente muestra las páginas de propiedades de un proyecto de Visual C++. En el panel de la izquierda, está seleccionada la **regla** *Directorios VC++* y en el de la derecha se muestran las propiedades asociadas a esa regla. Los valores `$(...)` desafortunadamente se denominan *macros*. *No* se trata de macros de C o C++, sino de constantes en tiempo de compilación. (Las macros se describen en la sección [Macros de la página de propiedades](#bkmkPropertiesVersusMacros) más adelante en este artículo).

![Páginas de propiedades del proyecto](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")

> [!WARNING]
> Se han quitado las configuraciones de **Propiedades comunes** de las versiones anteriores de Visual Studio. Para agregar una referencia a un proyecto, ahora se usa el cuadro de diálogo **Agregar referencia** igual que con los lenguajes administrados. Vea [Administrar referencias en un proyecto](/visualstudio/ide/managing-references-in-a-project).

#### <a name="to-set-a-property-for-a-project"></a>Para establecer una propiedad de un proyecto

1. Para la mayoría de los escenarios, se pueden establecer propiedades en el nivel de proyecto sin crear una hoja de propiedades personalizada. En el menú principal, seleccione **Proyecto &#124; Propiedades**, o bien haga clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones** y seleccione **Propiedades**.

2. Use los cuadros de lista **Configuración** y **Plataforma** de la parte superior del cuadro de diálogo para especificar a qué grupos de propiedades se deben aplicar los cambios. En muchos casos **Todas las plataformas** y **Todas las configuraciones** son la elección correcta. Para establecer las propiedades solo para algunas configuraciones, realice una selección múltiple de ellas en el **Administrador de propiedades** y, después, abra el menú contextual y seleccione **Propiedades**.

En el cuadro de diálogo **Páginas de propiedades** solo se muestran las páginas de propiedades que se aplican al proyecto actual. Por ejemplo, si el proyecto no tiene un archivo .idl, la página de propiedades de MIDL no se muestra.

Al resaltar una propiedad en una página de propiedades, puede presionar **F1** para ir al tema de referencia para obtener más información sobre el modificador de compilador o vinculador correspondiente.

Puede obtener más información sobre cada página de propiedades en estos temas:

- [Página de propiedades General (Proyecto)](../ide/general-property-page-project.md)

- [Página de propiedades General (Archivo)](../ide/general-property-page-file.md)

- [Páginas de propiedades Línea de comandos](../ide/command-line-property-pages.md)

- [Configuración del proyecto para una configuración de depuración de C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)

- [Página de propiedades NMake](../ide/nmake-property-page.md)

- [Páginas de propiedades Vinculador](../ide/linker-property-pages.md)

- [Páginas de propiedades Recursos](../ide/resources-property-pages.md)

- [Páginas de propiedades MIDL](../ide/midl-property-pages.md)

- [Página de propiedades Referencias Web](../ide/web-references-property-page.md)

- [Herramienta Generador de datos XML (Página de propiedades)](../ide/xml-data-generator-tool-property-page.md)

## <a name="to-quickly-browse-and-search-all-properties"></a>Para examinar y buscar rápidamente todas las propiedades

La página de propiedades **Todas las opciones** (bajo el nodo **Propiedades de configuración &#124; C/C++** del cuadro de diálogo **Páginas de propiedades**) proporciona una forma rápida de examinar y buscar las propiedades disponibles en el contexto actual. Tiene un cuadro de búsqueda especial y una sintaxis simple para ayudarle a filtrar los resultados:

Ningún prefijo:<br/>
Busque solo en los nombres de propiedad (subcadena sin distinción entre mayúsculas y minúsculas).

'/' o bien '-':<br/>
Buscar solo en modificadores de compilador (prefijo sin distinción entre mayúsculas y minúsculas)

v:<br/>
Busque solo en los valores (subcadena sin distinción entre mayúsculas y minúsculas).

##  <a name="bkmkPropertiesVersusMacros"></a> Macros de la página de propiedades

Una *macro* es una constante de tiempo de compilación que puede hacer referencia a un valor que se define por Visual Studio o el sistema MSBuild, o un valor definido por el usuario. Al utilizar macros en lugar de los valores incluidos en el código como, por ejemplo, rutas de directorio, le resultará más fácil compartir valores de propiedades entre máquinas y versiones de Visual Studio. Asimismo, podrá asegurarse de que la configuración del proyecto participa correctamente en la herencia de propiedades. Se puede usar el Editor de propiedades para ver los valores de todas las macros disponibles.

### <a name="predefined-macros"></a>Macros predefinidas

*macros globales*<br/>
Se aplica a todos los elementos de una configuración de proyecto. Tiene la sintaxis `$(name)`. Un ejemplo de una macro global es `$(VCInstallDir)`, que almacena el directorio raíz de la instalación de Visual Studio. Una macro global corresponde a `PropertyGroup` en MSBuild.

*macros de elemento*<br/>
Tiene la sintaxis `%(name)`. Para un archivo, una macro de elemento solo se aplica a ese archivo; por ejemplo, puede utilizar `%(AdditionalIncludeDirectories)` para especificar directorios de inclusión que solo se aplican a un archivo determinado. Esta clase de macro de elemento corresponde a metadatos `ItemGroup` en MSBuild. Cuando se utiliza en el contexto de una configuración de proyecto, se aplica una macro de elemento a todos los archivos de un tipo determinado. Por ejemplo, la propiedad de configuración **Definiciones de preprocesador** de C/C++ puede tomar una macro de elemento `%(PreprocessorDefinitions)` que se aplica a todos los archivos .cpp del proyecto. Esta clase de macro de elemento corresponde a metadatos `ItemDefinitionGroup` en MSBuild. Para obtener más información, consulte [Definiciones de elementos](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Macros definidas por el usuario

Se pueden crear *macros definidas por el usuario* para usarlas como variables en compilaciones de proyectos. Por ejemplo, puede crear una macro definida por el usuario que proporcione un valor a un paso de compilación personalizada o a una herramienta de compilación personalizada. Una macro definida por el usuario es un par de nombre y valor. En un archivo de proyecto, use la notación **$(**<em>nombre</em>**)** para acceder al valor.

La macro definida por el usuario se almacena en una hoja de propiedades. Si el proyecto todavía no contiene una hoja de propiedades, puede crear una siguiendo los pasos descritos en [Crear configuraciones de propiedad reutilizables](#bkmkPropertySheets).

##### <a name="to-create-a-user-defined-macro"></a>Para crear una macro definida por el usuario

1. En la ventana **Administrador de propiedades** (en la barra de menús, seleccione **Ver**, **Administrador de propiedades**), abra el menú contextual de una hoja de propiedades (su nombre termina en .user) y después seleccione Propiedades. Se abre el cuadro de diálogo **Páginas de propiedades** de esa hoja de propiedades.

1. En el panel de la izquierda del cuadro de diálogo, seleccione **Macros de usuario**. En el panel de la derecha, haga clic en el botón **Agregar macro** para abrir el cuadro de diálogo **Agregar macro de usuario**.

1. En el cuadro de diálogo, especifique un nombre y un valor para la macro. Opcionalmente, active la casilla **Establecer esta macro como variable de entorno en el entorno de compilación**.

## <a name="property-editor"></a>Editor de propiedades

Puede utilizar el editor de propiedades para modificar determinadas propiedades de cadena y seleccionar macros como valores. Para tener acceso al editor de propiedades, seleccione una propiedad en una página de propiedades y elija el botón de flecha abajo de la derecha. Si la lista desplegable contiene **\<Editar>**, podrá decidir si quiere que muestre el Editor de propiedades para esa propiedad.

![Menú desplegable&#95;Editor&#95;de propiedades](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")

En el Editor de propiedades, puede hacer clic en el botón **Macros** para ver las macros disponibles y sus valores actuales. En la ilustración siguiente se muestra el Editor de propiedades para la propiedad **Directorios de inclusión adicionales** después de haber hecho clic en el botón **Macros**. Cuando se activa la casilla **Heredar de primario o valores pred. del proyecto** y se agrega un valor nuevo, se anexa a cualquier valor que se está heredando actualmente. Si desactiva la casilla, el nuevo valor reemplaza los valores heredados. En la mayoría de los casos, deje la casilla activada.

![Editor de propiedades, Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")

##  <a name="bkmkPropertySheets"></a> Crear configuraciones de propiedad reutilizables

Aunque puede establecer propiedades "globales" por usuario y equipo, este es un proceso que ya no se recomienda. En su lugar, se recomienda usar el **Administrador de propiedades** para crear una *hoja de propiedades* para almacenar los valores para cada tipo de proyecto que se quiera reutilizar o compartir con otros usuarios. Las hojas de propiedades también hacen menos probable que la configuración de propiedades a otros tipos de proyecto se modifique accidentalmente. Las hojas de propiedades se describen con más detalle en [Crear configuraciones de propiedad reutilizables](#bkmkPropertySheets).

> [!IMPORTANT]
> **Los archivos .user y las razones por las que son problemáticos**
>
> En las versiones anteriores de Visual Studio se usaban hojas de propiedades globales que tenían una extensión de nombre de archivo .user y se encontraban en la carpeta \<PerfilDeUsuario>\AppData\Local\Microsoft\MSBuild\v4.0\. Ya no recomendamos estos archivos porque establecen propiedades para configuración de proyecto por usuario y por equipo. Estos valores "globales" pueden interferir con las compilaciones, especialmente cuando tenga como destino varias plataformas en el equipo de compilación. Por ejemplo, si tiene un proyecto MFC y un proyecto de Windows Phone, las propiedades .user no serían válidas para uno de ellos. Las hojas de propiedades reutilizables son más flexibles y más eficaces.
>
> Aunque los archivos .user todavía se instalan con Visual Studio y participan en la herencia de propiedades, están vacíos de forma predeterminada. El procedimiento recomendado es eliminar la referencia a ellos en el **Administrador de propiedades** para asegurarse de que los proyectos funcionan independientemente de cualquier configuración por usuario y por equipo. Esto es importante para asegurar un comportamiento correcto en un entorno SCC (control de código fuente).

Para mostrar el **Administrador de propiedades**, en la barra de menús, seleccione **Ver**, **Otras ventanas**, **Administrador de propiedades**.

Si tiene un conjunto de propiedades común que usa con frecuencia y que quiera aplicar a varios proyectos, puede usar el **Administrador de propiedades** para capturarlas en un archivo de *hoja de propiedades* reutilizable, que por convención tiene una extensión de nombre de archivo .props. Puede aplicar la hoja (u hojas) a nuevos proyectos para que no tenga que establecer sus propiedades desde cero. Para acceder al **Administrador de propiedades**, en la barra de menús, seleccione **Ver**, **Administrador de propiedades**.

![Menú contextual del Administrador de propiedades](../ide/media/sharingnew.png "SharingNew")

En cada nodo de configuración, podrá ver los nodos para cada hoja de propiedades que se aplica a esa configuración. El sistema agrega hojas de propiedades que establecen valores en función de las opciones que se elijan en el Asistente para aplicaciones al crear el proyecto. Haga clic con el botón derecho en cualquier nodo y seleccione Propiedades para ver las propiedades que se aplican a ese nodo. Todas las hojas de propiedades se importan de manera automática en la hoja de propiedades "maestra" del proyecto (ms.cpp.props) y se evalúan en el orden en que aparecen en el Administrador de propiedades. Se pueden mover para cambiar el orden de evaluación. Las hojas de propiedades que se evalúan después invalidarán los valores de las hojas evaluadas anteriormente.

Si hace clic en **Agregar nueva hoja de propiedades de proyecto** y selecciona, por ejemplo, la hoja de propiedades MyProps.props, aparecerá un cuadro de diálogo de página de propiedades. Observe que se aplica a la hoja de propiedades MyProps; los cambios que realice se escriben en la hoja, no en el archivo de proyecto (.vcxproj).

Las propiedades en una hoja de propiedades se invalidan si la misma propiedad se establece directamente en el archivo .vcxproj.

Puede importar una hoja de propiedades con tanta frecuencia como sea necesaria. Varios proyectos de una solución pueden heredar valores de la misma hoja de propiedades y un proyecto puede tener varias hojas. Una hoja de propiedades en sí misma puede heredar la configuración de otra hoja de propiedades.

También puede crear una hoja de propiedades para varias configuraciones. Para ello, cree una hoja de propiedades para cada configuración, abra el menú contextual para una de ellas, seleccione **Agregar hoja de propiedades existente** y, después, agregue las demás hojas. Sin embargo, si utiliza una hoja de propiedades comunes, tenga en cuenta que, cuando se establece una propiedad, obtiene el conjunto de todas las configuraciones a las que se aplica la hoja y el IDE no muestra los proyectos u hojas de propiedades que heredan valores de una hoja de propiedades determinada.

En soluciones grandes que tendrán muchos proyectos, puede ser útil crear una hoja de propiedades en el nivel de solución. Al agregar un proyecto a la solución, use el **Administrador de propiedades** para agregar esa hoja de propiedades al proyecto. Si se solicita en el nivel de proyecto, puede agregar una nueva hoja de propiedades para establecer valores específicos del proyecto.

> [!IMPORTANT]
> Los archivos .props no participan de forma predeterminada en el control de código fuente porque no se crean como elemento del proyecto. Puede agregar manualmente el archivo como elemento de la solución si desea incluirlo en el control de código fuente.

#### <a name="to-create-a-property-sheet"></a>Para crear una hoja de propiedades

1. En la barra de menús, seleccione **Ver**, **Administrador de propiedades**. Se abrirá el **Administrador de propiedades**.

2. Para definir el ámbito de la hoja de propiedades, seleccione el elemento al que se aplica. Puede ser una configuración concreta u otra hoja de propiedades. Abra el menú contextual para este elemento y después seleccione **Agregar nueva hoja de propiedades de proyecto**. Especifique un nombre y una ubicación.

3. En el **Administrador de propiedades**, abra la hoja de propiedades nueva y después establezca las propiedades que quiera incluir.

##  <a name="bkmkPropertyInheritance"></a> Herencia de propiedades

Las propiedades de proyecto se dividen en capas. Cada capa hereda los valores de la capa anterior; sin embargo, un valor heredado puede invalidarse estableciendo la propiedad explícitamente. Este es el árbol básico de herencia:

1. Configuración predeterminada del conjunto de herramientas de MSBuild CPP (..\Archivos de programa\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, que importa el archivo .vcxproj).

2. Hojas de propiedades

3. Archivo .vcxproj. (Puede invalidar la configuración predeterminada y de la hoja de propiedades).

4. Metadatos de elemento

> [!TIP]
> En una página de propiedades, una propiedad de `bold` se define en el contexto actual. Se hereda una propiedad en fuente normal.

Un archivo de proyecto (.vcxproj) importa otras hojas de propiedades en el tiempo de compilación. Después de importar todas las hojas de propiedades, el archivo del proyecto se evalúa y se usa la última definición de los valores de propiedades. En ocasiones, es útil ver el archivo expandido para determinar cómo se hereda un valor de propiedad especificado. Para ver la versión ampliada, escriba el siguiente comando en un símbolo del sistema de Visual Studio. (Cambie los nombres de archivo de marcador de posición a los que desea usar).

**msbuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

Los archivos de proyecto expandidos pueden ser de gran tamaño y difíciles de comprender a menos que esté familiarizado con MSBuild. A continuación se muestra la estructura básica de un archivo de proyecto:

1. Propiedades fundamentales del proyecto que no se exponen en el IDE.

2. Importación de Microsoft.cpp.default.props, que define algunas propiedades básicas independientes del conjunto de herramientas.

3. Página de propiedades de configuración global (expuestas como **PlatformToolset** y propiedades predeterminadas de **Proyecto** en la página **Configuración general**. Estas propiedades determinan qué conjunto de herramientas y hojas de propiedades intrínsecas se importan en Microsoft.cpp.props en el paso siguiente.

4. Importación de Microsoft.cpp.props, que establece la mayoría de los valores predeterminados del proyecto.

5. Importación de todas las hojas de propiedades, incluidos los archivos .user. Estas hojas de propiedades pueden reemplazar todo excepto las propiedades predeterminadas **PlatformToolset** y **Project**.

6. El resto de propiedades de configuración del proyecto. Estos valores pueden invalidar lo que estaba establecido en las hojas de propiedades.

7. Elementos (archivos), junto con sus metadatos. Estas son siempre la última palabra en las reglas de evaluación de MSBuild, aunque se produzcan antes de otras propiedades e importaciones.

Para obtener más información, consulte [Propiedades de MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>Adición de un directorio de inclusión al conjunto de directorios predeterminados

Cuando agrega un directorio de inclusión a un proyecto, es importante no invalidar todos los directorios predeterminados. La forma correcta de agregar un directorio es anexar la ruta de acceso nueva, por ejemplo "C:\MyNewIncludeDir\", y luego anexar la macro **$(IncludePath)** al valor de propiedad.

## <a name="setting-environment-variables-for-a-build"></a>Establecer variables de entorno para una compilación

El compilador de Visual C++ (cl.exe) reconoce determinadas variables de entorno, en concreto LIB, LIBPATH, PATH e INCLUDE. Al compilar con el IDE, las propiedades establecidas en la página de propiedades [Directorios de VC++](../ide/vcpp-directories-property-page.md) se usan para establecer esas variables de entorno. Si los valores LIB, LIBPATH e INCLUDE se han definido, por ejemplo mediante el símbolo del sistema del desarrollador, estos se reemplazarán por los valores de las propiedades de MSBuild correspondientes. La compilación luego antepone el valor de la propiedad de directorios ejecutable de los directorios VC++ en PATH. Puede establecer una variable de entorno definida por el usuario si crea una macro definida por el usuario y activa la casilla **Establecer esta macro como variable de entorno en el entorno de compilación**.

## <a name="setting-environment-variables-for-a-debugging-session"></a>Establecimiento de variables de entorno para una sesión de depuración

En el panel de la izquierda del cuadro de diálogo **Páginas de propiedades** del proyecto, expanda **Propiedades de configuración** y, después, seleccione **Depuración**.

En el panel de la derecha, modifique las opciones **Entorno** o **Combinar entorno**, y después haga clic en el botón **Aceptar**.

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>Modificar las propiedades y los destinos sin cambiar el archivo de proyecto

Puede invalidar las propiedades y los destinos del proyecto desde la línea de comandos de MSBuild sin cambiar el archivo de proyecto. Esto es útil cuando se quieren aplicar algunas propiedades de manera ocasional o temporal. Se presuponen ciertos conocimientos de MSBuild. Para obtener más información, vea [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Para crear el archivo .props o .targets, puede usar el Editor XML de Visual Studio o cualquier editor de texto. No use el **Administrador de propiedades** en este escenario ya que agrega las propiedades al archivo de proyecto.

*Para reemplazar las propiedades del proyecto:*

1. Cree un archivo .props en el que se especifiquen las propiedades que se quieren invalidar.

1. Desde el símbolo del sistema: establezca ForceImportBeforeCppTargets="C:\sources\my_props.props".

*Para reemplazar los destinos del proyecto:*

1. Cree un archivo .targets con su implementación o un destino concreto.

2. Desde el símbolo del sistema: establezca ForceImportAfterCppTargets ="C:\sources\my_target.targets".

También puede establecer cualquiera de las opciones en la línea de comandos de msbuild mediante la opción /p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

El reemplazo de propiedades y destinos de esta manera equivale a agregar las importaciones siguientes a todos los archivos .vcxproj de la solución:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```

## <a name="see-also"></a>Vea también

[Creación y administración de proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Estructura de archivo .vcxproj y .props](vcxproj-file-structure.md)<br/>
[Archivos XML de página de propiedades](property-page-xml-files.md)<br/>
