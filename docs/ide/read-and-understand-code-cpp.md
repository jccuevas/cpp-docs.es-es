---
title: Lectura y reconocimiento de código C++ en Visual Studio
description: Use el editor de código de C++ en Visual Studio para dar formato al código y entenderlo.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377299"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Lectura y reconocimiento de código C++ en Visual Studio

El editor de código de C++ y el IDE de Visual Studio proporcionan muchas ayudas a la programación. Algunas son exclusivas de C++ y algunas son básicamente iguales para todos los lenguajes de Visual Studio. Para obtener más información sobre las características compartidos, vea [Características del editor de código](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Uso de colores

Visual Studio colorea elementos de la sintaxis para distinguir los diferentes tipos de símbolos, como palabras clave del lenguaje, nombres de tipos, nombres de variables, parámetros de función, literales de cadena, etc.

![Uso de colores para el código](../ide/media/code-outline-colorization.png "Coloración C++")

El código sin usar (por ejemplo, el código de una instrucción #if 0) presenta un color más atenuado.

![Código inactivo](../ide/media/inactive-code-cpp.png "C++ código inactivo")

Los colores se pueden personalizar; para ello, escriba "Fuentes" en **Inicio rápido** y, después, elija **Fuentes y colores**. En el cuadro de diálogo **Fuentes y colores**, desplácese hasta las opciones de C /C++ y, después, elija una fuente o un color personalizados.

## <a name="outlining"></a>esquematizar

Haga clic con el botón derecho en un archivo de código fuente y seleccione **Esquematización** para contraer o expandir bloques de código o regiones personalizadas para que sea más fácil examinar únicamente el código que le interesa. Para obtener más información, vea [Esquematización](/visualstudio/ide/outlining).

![Esquema de&#43;&#43; C](../ide/media/vs2015_cpp_outlining.png "esquematizar")

Cuando el cursor se coloca delante de una llave ("{" o "}"), el editor resalta su homólogo coincidente.

Otras opciones de esquematización se encuentran en **Editar** > **esquematización** en el menú principal.

## <a name="line-numbers"></a>Números de línea

Puede agregar números de línea a su proyecto yendo a **Opciones** > **Options** > de herramientas**Editor** > de texto**Todos los idiomas** > **generales** o buscando "line num" con Inicio **rápido (Ctrl + Q)**. Se pueden establecer números de línea para todos los lenguajes o para lenguajes concretos, incluido C++.

## <a name="scroll-and-zoom"></a>Desplazamiento y zoom

Puede acercar o alejar el editor; para ello, presione la tecla **Ctrl** y desplácese con la rueda del mouse. También puede hacer zoom usando la opción de zoom que hay en la esquina inferior izquierda.

![C&#43;&#43; Zoom Control](../ide/media/zoom-control.png "Control de zoom")

El **modo de mapa** de la barra de desplazamiento permite desplazarse y examinar rápidamente un archivo de código sin abandonar la ubicación actual. Puede hacer clic en cualquier parte del mapa de código para ir directamente a esa ubicación.

![Mapa de código en&#43;&#43;C](../ide/media/vs2015-cpp-code-map.png "Mapa de código")

Para activar el **modo de mapa**, escriba "map" en el cuadro de búsqueda Inicio **rápido** de la barra de herramientas principal y elija Usar modo de mapa de **desplazamiento**. Para obtener más información, vea [Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Si **Modo de mapa** está desactivado, la barra de desplazamiento sigue resaltando los cambios realizados en el archivo. El color verde señala los cambios guardados y el amarillo, los no guardados.

## <a name="quick-info-and-parameter-info"></a>Información rápida e información de parámetros

Mantenga el puntero sobre cualquier variable, función u otro símbolo para obtener información sobre dicho elemento, incluida la declaración correspondiente y cualquier comentario que haya justo antes de él.

::: moniker range="vs-2019"

![Información rápida en&#43;&#43;C](../ide/media/quick-info-vs2019.png "Información rápida")

La información sobre herramientas **Información rápida** dispone de un vínculo **Buscar en línea**. Vaya a**Opciones** > de **herramientas** > **Editor** > de texto**C++** > **View** para especificar el proveedor de búsqueda.

Si hay un error en el código, puede mantener el puntero sobre él e **Información rápida** mostrará el mensaje de error. También puede encontrar el mensaje de error en la ventana Lista de errores.

![Información rápida sobre el error](../ide/media/quickinfo-on-error.png "Información rápida sobre el error")

::: moniker-end

::: moniker range="<=vs-2017"

![Información rápida en&#43;&#43;C](../ide/media/quick-info.png "Información rápida")

Si hay un error en el código, puede mantener el puntero sobre él e **Información rápida** mostrará el mensaje de error. También puede encontrar el mensaje de error en la ventana Lista de **errores.**

![Información rápida sobre el error](../ide/media/quickinfo-on-error.png "Información rápida sobre el error")

::: moniker-end

Cuando se llama a una función, **Información de parámetros** muestra los tipos de parámetros y el orden en el que está previsto que aparezcan.

![Información de parámetros en C&#43;&#43;](../ide/media/parameter-info.png "Información de parámetros")

## <a name="peek-definition"></a>Ver la definición

Mantenga el puntero sobre una declaración de variable o función, haga clic con el botón derecho y, después, seleccione **Ver la definición** para ver una vista insertada de su definición correspondiente sin tener que abandonar la ubicación actual. Para obtener más información, vea [Ver la definición (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Definición de C&#43;&#43; Peek](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>Ayuda F1

Coloque el cursor sobre o justo después de cualquier tipo, palabra clave o función y presione **F1** para ir directamente al tema de referencia relevante en docs.microsoft.com. **F1** también funciona en elementos de la lista de errores y en muchos cuadros de diálogo.

## <a name="class-view"></a>Vista de clases

En **Vista de clases** se muestra un conjunto de árboles (donde se pueden realizar búsquedas) con todos los símbolos de código, sus ámbitos y sus jerarquías de elementos primarios y secundarios, todo ello organizado por proyectos. Puede configurar qué **Vista de clases** se va a mostrar en **Configuración de vista de clases** (haga clic en el icono de engranaje en la parte superior de la ventana).

![Vista de clase en&#43;&#43;C](../ide/media/class-view.png "Vista de clases")

## <a name="generate-graph-of-include-files"></a>Generar gráfico de archivos de inclusión

Haga clic con el botón derecho en un archivo de código del proyecto y seleccione **Generar gráfico de archivos de inclusión** para ver un gráfico de los archivos que otros archivos incluyen.

![C&#43;&#43; gráfico de archivos de inclusión](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Ver jerarquía de llamadas

Haga clic con el botón derecho en cualquier llamada a función y vea una lista recursiva de todas las funciones a las que llama y de todas las funciones que la llaman. Cada una de las funciones de la lista se pueden expandir de la misma manera. Para obtener más información, vea [Jerarquía de llamadas](/visualstudio/ide/reference/call-hierarchy).

![C Jerarquía de llamadas&#43;&#43; ](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Consulte también

[Escribir y refactorizar código (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navegación en el código de C++ en Visual Studio](navigate-code-cpp.md)</br>
[Colaborar con Live Share para C++](live-share-cpp.md)
