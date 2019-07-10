---
title: Navegación en el código de C++ en Visual Studio
description: Use diversas herramientas de Visual Studio para navegar por el código base de C++.
ms.date: 05/28/2019
ms.openlocfilehash: c2d3a1aa4a26cb820ff4a1e87d6eae88b1b8e739
ms.sourcegitcommit: 96f48079cdc402e4c2c1578d1f1eed4846a484dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2019
ms.locfileid: "67576525"
---
# <a name="navigate-c-code-in-visual-studio"></a>Navegación en el código de C++ en Visual Studio

Visual Studio proporciona un conjunto de herramientas que puede usar para navegar por el código base de manera rápida y eficaz.

## <a name="open-an-included-file"></a>Abrir un archivo incluido

Haga clic con el botón derecho en una directiva de `#include` y seleccione **Ir al documento**. O bien, seleccione **F12** con el cursor sobre esa línea para abrir el archivo.

![Opción de menú Ir al documento de C&#43;&#43;](../ide/media/go-to-document.png "Ir al documento")

## <a name="toggle-headercode-file"></a>Alternar archivo de encabezado/código

Puede cambiar entre un archivo de encabezado y su archivo de origen correspondiente. Haga clic con el botón derecho en cualquier lugar del archivo y seleccione **Alternar archivo de encabezado/código**. O bien, puede seleccionar **Ctrl+K**, **Ctrl+O**.

## <a name="go-to-definitiondeclaration"></a>Ir a definición/declaración

Para ir a la definición de un símbolo de código, haga clic con el botón derecho en el editor y seleccione **Ir a definición** o seleccione **F12**. Puede ir a una declaración de una manera similar, con un clic con el botón derecho para abrir el menú contextual o seleccionando **Ctrl+F12**.

![Ir a definición de C&#43;&#43;](../ide/media/go-to-def.png "Ir a definición")

## <a name="go-to"></a>Ir a

**Ir a** hace referencia a un conjunto de características de navegación donde cada una proporciona un determinado tipo de resultado según los filtros que se especifiquen. 

Puede abrir la opción **Ir a** con **Ctrl+,** . Esta acción crea un cuadro de búsqueda en el documento que está editando.

![Ir a de C&#43;&#43;](../ide/media/go-to-cpp.png "Ir a")

**Ir a** incluye estos filtros de búsqueda:

- **Ir a la línea** (**Ctrl+G**): salta rápidamente a otra línea en el documento actual.
- **Ir a todo** (**Ctrl+,** ) o (**Ctrl+T**): Los resultados de la búsqueda incluyen todo lo que sigue.
- **Ir al archivo** (**Ctrl 1, F**): buscar archivos en la solución.
- **Ir al tipo** (**Ctrl 1, T**): los resultados de la búsqueda incluyen:
  - Clases, estructuras y enumeraciones.
  - Interfaces y delegados (solo código administrado).
- **Ir al miembro** (**Ctrl 1, M**): los resultados de la búsqueda incluyen:
  - Variables y funciones globales.
  - Variables miembro de clase y funciones miembro.
  - Constantes.
  - Elementos de enumeración.
  - Propiedades y eventos.
- **Ir al símbolo** (**Ctrl 1, S**): los resultados de la búsqueda incluyen:
  - Resultados de Ir al tipo e Ir al miembro.
  - Todas las demás construcciones del lenguaje C++, que incluyen las macros.

Al invocar **Ir a** con **Ctrl +** por primera vez, **Ir a todo** se activa (sin filtros en los resultados de la búsqueda). Luego, puede seleccionar el filtro que quiera con los botones junto al cuadro de búsqueda. También puede invocar un filtro específico usando el método abreviado de teclado correspondiente. Si lo hace, se abre el cuadro de búsqueda **Ir a** con ese filtro ya seleccionado. Todos los métodos abreviados de teclado son configurables.

Para aplicar un filtro de texto, inicie la consulta de búsqueda con el carácter correspondiente del filtro, seguido de un espacio. (En **Ir a la línea**, el espacio se puede omitir opcionalmente). Estos filtros de texto están disponibles:

- Ir a todo: (sin filtro de texto)
- Ir a número de línea: :
- Ir al archivo: f
- Ir al tipo: t
- Ir al miembro: m
- Ir al símbolo: #

En el siguiente ejemplo se muestran los resultados de una operación *Ir al archivo* con el filtro "f":

![Menú Ir a de C&#43;&#43;](../ide/media/vs2017-go-to-results.png "Menú Ir a")

Para ver la lista de filtros de texto, escriba un signo de interrogación de cierre (?) seguido de un espacio. También puede tener acceso a los comandos de **Ir a** mediante el menú **Editar**. Esta es otra forma de acordarse de los principales métodos abreviados de teclado de **Ir a**.

![Menú Ir a de C&#43;&#43;](../ide/media/go-to-menu-cpp.png "Menú Ir a")

## <a name="find-or-find-in-files"></a>Buscar o Buscar en archivos

Puede buscar cualquier tipo de texto en la solución con las opciones **Buscar** (**Ctrl+F**) o **Buscar en archivos** (**Ctrl+Mayús+F**).

La **búsqueda** se puede acotar a una selección, al documento actual, a todos los documentos abiertos, al proyecto actual o a la solución entera. Se pueden usar expresiones regulares y texto sin formato. También se resaltan todas las coincidencias automáticamente en el IDE.

![Buscar en C&#43;&#43;](../ide/media/find-cpp.png "Buscar")

**Buscar en archivos** es una versión más eficaz de **Buscar** que muestra los resultados en la ventana **Resultados de la búsqueda**. Puede buscar dependencias de código externas, filtrar por tipos de archivos y mucho más. 

![Buscar en archivos en C&#43;&#43;](../ide/media/find-in-files-cpp.png "Buscar en archivos")

Los resultados de **Buscar en archivos** se pueden organizar en dos ventanas. Se pueden anexar resultados de varias búsquedas de manera conjunta. Seleccione un resultado para ir a esa ubicación en el archivo.

![Buscar en archivos en C&#43;&#43;](../ide/media/vs2017-find-in-files-results.png "Buscar en archivos")

Para obtener más información, vea [Buscar en archivos](/visualstudio/ide/find-in-files) en la documentación de Visual Studio.

## <a name="find-all-references"></a>Buscar todas las referencias

Para buscar todos los usos de un símbolo en el código base, coloque el símbolo de intercalación en el símbolo, haga clic con el botón derecho y seleccione **Buscar todas las referencias**. Puede filtrar, ordenar o agrupar los resultados de muchas maneras diferentes. Los resultados se van rellenando de forma incremental. Se clasifican como lecturas o escrituras para ayudarle a ver qué hay en la solución en contraposición a los encabezados del sistema o a otras bibliotecas.

![Buscar todas las referencias de C&#43;&#43;](../ide/media/find-all-references-results-cpp.png "Buscar todas las referencias")

Los resultados se pueden agrupar por las siguientes categorías:

- Proyecto y luego Definición
- Solo definición
- Definición y luego Proyecto
- Definición y luego Ruta de acceso
- Definición, Proyecto y luego Ruta de acceso

 #### <a name="filter-results"></a>Filtrar resultados

Para filtrar los resultados, mantenga el puntero sobre una columna y seleccione el icono de filtro que aparece. Puede filtrar los resultados de la primera columna para ocultar cosas como referencias de cadenas y de comentarios que probablemente no le interese ver.

![Filtros de Buscar todas las referencias de C&#43;&#43;](../ide/media/find-all-references-filters-cpp.png "Filtros de Buscar todas las referencias")

- **Resultados confirmados**: referencias de código reales al símbolo que se está buscando. Por ejemplo, si se busca una función miembro llamada `Size`, se devuelven todas las referencias a `Size` que coinciden con el ámbito de la clase que define `Size`.

- **Resultados con confirmación anulada**: este filtro está desactivado de manera predeterminada porque muestra los símbolos cuyos nombres coinciden con el símbolo que se está buscando, pero que no son referencias reales. Por ejemplo, si tiene dos clases (cada una de las cuales define una función miembro llamada `Size`) y realiza una búsqueda de `Size` en una referencia de un objeto de `Class1`, todas las referencias a `Size` que se hagan desde `Class2` aparecerán como confirmaciones canceladas.

- **Resultados sin procesar**: las operaciones **Buscar todas las referencias** pueden tardar tiempo en completarse cuando las bases de código son especialmente grandes, lo que hace que la lista de resultados muestre resultados "sin procesar" aquí. Los resultados sin procesar coinciden con el nombre del símbolo que se está buscando, pero aún no se han confirmado como referencias de código reales. Este filtro se puede activar para obtener resultados más rápidamente. Recuerde únicamente que es posible que algunos resultados no sean referencias reales.

 #### <a name="sort-results"></a>Ordenar resultados

Los resultados se pueden ordenar por cualquier columna al seleccionar esa columna. Puede intercambiar entre orden ascendente o descendente si vuelve a seleccionar la columna.

## <a name="navigation-bar"></a>Barra de navegación

Puede navegar a la definición de un tipo en un archivo, o a miembros de tipo, mediante la **barra de navegación** que hay encima de la ventana del editor.

![Barra de navegación de C&#43;&#43;](../ide/media/navbar-cpp.png "Barra de navegación")

## <a name="see-also"></a>Vea también

- [Lectura y reconocimiento de código C++](read-and-understand-code-cpp.md)</br>
- [Edición y refactorización de código C++](read-and-understand-code-cpp.md)</br>
- [Colaborar con Live Share para C++](live-share-cpp.md)