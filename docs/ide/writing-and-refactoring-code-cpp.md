---
title: Escribir y refactorizar código (C++)
description: Use el editor de código de C++ en Visual Studio para dar formato al código, recorrerlo, entenderlo y refactorizarlo.
ms.date: 05/14/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: 04f738cd6fdd456c432c334df42f37339e7fa49e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182635"
---
# <a name="writing-and-refactoring-code-c"></a>Escribir y refactorizar código (C++)

El editor de código de C++ y el IDE de Visual Studio proporcionan muchas ayudas a la programación. Algunas son exclusivas de C++ y algunas son básicamente iguales para todos los lenguajes de Visual Studio. Para obtener más información sobre las características compartidos, vea [Características del editor de código](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Las opciones para habilitar y configurar características específicas de C++ se encuentran en **Herramientas &#124; Opciones &#124; Editor de texto &#124; C/C++**. Después de elegir la opción que quiere establecer, puede obtener más ayuda si presiona **F1** cuando el cuadro de diálogo tenga el foco. Para las opciones de formato de código generales, escriba `Editor C++` en el **Inicio rápido**.

Las características experimentales, que se podrían incluir o no en una versión futura de Visual Studio, se encuentran en el cuadro de diálogo [Editor de texto C++ Experimental](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental). En Visual Studio 2017, se puede habilitar **IntelliSense predictivo** en este cuadro de diálogo.

## <a name="adding-new-files"></a>Agregar archivos nuevos

Para agregar archivos nuevos a un proyecto, haga clic con el botón derecho en el nodo de proyecto en el Explorador de soluciones y seleccione **Agregar &#124; Nuevo**.

## <a name="formatting-options"></a>Opciones de formato

Para establecer opciones de formato, como sangrías, finalización de llave y coloración, escriba "Formato de C++" en la ventana **Inicio rápido**. En Visual Studio 2017, versión 15.7 y posteriores se admite ClangFormat. Se puede configurar en la [página de propiedades Formato de C/C++](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting) en **Herramientas &#124; Opciones &#124; Editor de texto &#124; C/C++ &#124; Formato**.

![Opciones de formato de C++](media/cpp-formatting-options.png)

## <a name="intellisense"></a>IntelliSense

IntelliSense es el nombre de un conjunto de características que proporcionan información en línea acerca de miembros, tipos y sobrecargas de función. La siguiente ilustración muestra la lista desplegable de miembros que aparece a medida que escribe. Puede presionar la tecla TAB para escribir el texto del elemento seleccionado en el archivo de código.

![C&#43; &#43; lista desplegable lista de miembros](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

Para obtener información completa, vea [IntelliSense para Visual C++](/visualstudio/ide/visual-cpp-intellisense).

## <a name="insert-snippets"></a>Insertar fragmentos de código

Un fragmento de código es una parte de código fuente predefinida. Haga clic con el botón derecho en un único punto o en el texto seleccionado para insertar un fragmento de código o rodear el texto seleccionado con el fragmento de código. La siguiente ilustración muestra los tres pasos necesarios para envolver una instrucción seleccionada con un bucle for. Las partes resaltadas en amarillo de la imagen final son campos que se pueden editar y a los que puede acceder con la tecla TAB. Para obtener más información, vea [Fragmentos de código](/visualstudio/ide/code-snippets).

![Visual C&#43; &#43; Lista desplegable Insertar fragmento de código](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

## <a name="add-class"></a>Agregar clase

Agregue una clase nueva desde el menú **Proyecto** mediante el Asistente para clases.

![Agregar nueva clase en Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

También puede usar el Asistente para clases para modificar o examinar una clase existente.

![Visual C&#43; &#43; Asistente para clases](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

Para obtener más información, vea [Agregar funcionalidad con los asistentes para código (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="refactoring"></a>Refactorización

Las refactorizaciones están disponibles bajo el menú contextual Acción rápida, o bien haciendo clic en una [bombilla](/visualstudio/ide/perform-quick-actions-with-light-bulbs) en el editor.  Algunas se encuentran en el menú **Editar > Refactorizar**.  Entre ellas se incluyen:

* [Cambiar nombre](refactoring/rename.md)
* [Extraer función](refactoring/extract-function.md)
* [Implementar virtuales puras](refactoring/implement-pure-virtuals.md)
* [Crear declaración o definición](refactoring/create-declaration-definition.md)
* [Mover definición de función](refactoring/move-definition-location.md)
* [Convertir en literal de cadena sin formato](refactoring/convert-to-raw-string-literal.md)
* [Cambiar firma](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>Navegar y comprender

Visual C++ comparte muchas características de exploración de código con otros lenguajes. Para obtener más información, vea [Navegación en el código](/visualstudio/ide/navigating-code) y [Visualización de la estructura del código mediante distintas ventanas de herramienta](/visualstudio/ide/viewing-the-structure-of-code).

## <a name="quickinfo"></a>InformaciónRápida

Coloque el mouse sobre una variable para ver su información de tipo.

![Visual C&#43;&#43; InformaciónRápida](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

## <a name="open-document-navigate-to-header"></a>Abrir documento (Ir a encabezado)

Haga clic con el botón derecho en el nombre del encabezado en una directiva `#include` y abra el archivo de encabezado.

![Visual C&#43; &#43; Opción de menú Abrir documento](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

## <a name="peek-definition"></a>Definición de Peek

Mantenga el puntero sobre una declaración de variable o función, haga clic con el botón derecho y, después, seleccione **Ver la definición** para ver una vista insertada de su definición. Para obtener más información, vea [Ver la definición (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Visual C&#43;&#43; Ver la definición](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="go-to-definition"></a>Ir a definición

Mantenga el puntero sobre una declaración de variable o función, haga clic con el botón derecho y, después, seleccione **Ir a definición** para abrir el documento donde se define el objeto.

## <a name="view-call-hierarchy"></a>Ver jerarquía de llamadas

Haga clic con el botón derecho en cualquier llamada a función y vea una lista recursiva de todas las funciones a las que llama y de todas las funciones que la llaman. Cada una de las funciones de la lista se pueden expandir de la misma manera. Para obtener más información, vea [Jerarquía de llamadas](/visualstudio/ide/reference/call-hierarchy).

![Visual C&#43;&#43; Jerarquía de llamadas](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="toggle-header--code-file"></a>Alternar archivo de encabezado/código

Haga clic con el botón derecho en **Alternar archivo de encabezado/código** para alternar entre un archivo de encabezado y su archivo de código asociado.

## <a name="outlining"></a>esquematizar

Haga clic con el botón derecho en un archivo de código fuente y seleccione **Esquematización** para contraer o expandir definiciones o regiones personalizadas para que sea más fácil examinar solo las partes que le interesan. Para obtener más información, vea [Esquematización](/visualstudio/ide/outlining).

![Visual C&#43;&#43; Esquematización](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

## <a name="scrollbar-map-mode"></a>Modo de mapa de barra de desplazamiento

El modo de mapa de barra de desplazamiento permite desplazarse y examinar rápidamente un archivo de código sin abandonar realmente su ubicación actual. También puede hacer clic en cualquier parte del mapa de código para ir directamente a esa ubicación. Para obtener más información, vea [Cómo: Seguimiento del código mediante la personalización de la barra de desplazamiento](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

![Mapa de código en Visual C&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

## <a name="generate-graph-of-include-files"></a>Generar gráfico de archivos de inclusión

Haga clic con el botón derecho en un archivo de código del proyecto y seleccione **Generar gráfico de archivos de inclusión** para ver un gráfico de los archivos que otros archivos incluyen.

![Visual C&#43; &#43; Gráfico de archivos de inclusión](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="f1-help"></a>F1 Ayuda

Coloque el cursor encima o justo después de cualquier tipo, palabra clave o función, y presione F1 para ir directamente al tema de referencia pertinente en docs.microsoft.com. F1 también funciona en elementos de la lista de errores y en muchos cuadros de diálogo.

## <a name="quick-launch"></a>Inicio rápido

Para navegar fácilmente hasta cualquier ventana o herramienta de Visual Studio, simplemente escriba su nombre en la ventana Inicio rápido situada en la esquina superior derecha de la interfaz de usuario. Se filtrará la lista de finalización automática a medida que escriba.

![Inicio rápido de Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
