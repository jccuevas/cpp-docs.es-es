---
title: Filtrar Incluir recursos en tiempo de compilación (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 5768347c32b1856da16310f29e7a4257e18b6a93
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676466"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Procedimiento Incluir recursos en tiempo de compilación (C++)

De forma predeterminada todos los recursos en se encuentran en el archivo de script (.rc) de un recurso, sin embargo, hay muchas razones para incluir recursos en un archivo distinto del archivo .rc principal:

- Para agregar comentarios a instrucciones de recursos que no se eliminan al guardar el archivo .rc.

- Para incluir recursos que ya se ha desarrollado y probado y no necesitan modificación. Los archivos que se incluyen, pero no tienen una extensión .rc no ser editables por los editores de recursos.

- Para incluir recursos que estén siendo utilizados por proyectos diferentes o que forman parte de un sistema de control de versiones de código fuente. Estos recursos deben existir en una ubicación central donde las modificaciones afectarán a todos los proyectos.

- Para incluir recursos (por ejemplo, recursos RCDATA) que están en un formato personalizado. Los recursos RCDATA tienen requisitos especiales donde no se puede utilizar una expresión como un valor para el `nameID` campo.

Si tiene secciones en los archivos .rc que cumplen alguna de estas condiciones, colocar estas secciones en uno o varios archivos .rc independientes e incluyen en el proyecto con el **incluye recursos** cuadro de diálogo.

## <a name="resource-includes"></a>Inclusión de recursos

Puede agregar recursos de otros archivos al proyecto en tiempo de compilación enumerándolos en el **Rectivas de tiempo** cuadro el **incluye recursos** cuadro de diálogo. Use la **incluye recursos** cuadro de diálogo para modificar el trabajo habitual del entorno de proyecto de almacenamiento de todos los recursos en el archivo .rc del proyecto y todos [símbolos](../windows/symbols-resource-identifiers.md) en `Resource.h`.

Para empezar, abra el **incluye recursos** haciendo clic en un archivo .rc en el cuadro de diálogo [vista de recursos](../windows/resource-view-window.md), seleccione **incluye recursos** y tenga en cuenta las siguientes propiedades:

| Property | Descripción |
|---|---|
| **Archivo de encabezado de símbolos** | Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de símbolos para los archivos de recursos.<br/><br/>Para obtener más información, consulte [cambiar los archivos de encabezado de los nombres de símbolos](../windows/changing-the-names-of-symbol-header-files.md). |
| **Directivas de símbolos de solo lectura** | Permite incluir archivos de encabezado que contienen los símbolos que no deberían modificarse. Por ejemplo, los archivos de símbolos para compartirse con otros proyectos. Esto también puede incluir archivos .h de MFC.<br/><br/>Para obtener más información, consulte [símbolos incluidos compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Directivas de tiempo de compilación** | Permite incluir archivos de recursos creados y editados con independencia de los recursos en el archivo principal de recursos, contienen las directivas de tiempo de compilación (por ejemplo, las directivas que se incluyen de forma condicional recursos), o los recursos en un formato personalizado. También puede usar el **cuadro directivas de tiempo de compilación** para incluir archivos de recursos MFC estándares. |

> [!NOTE]
> Las entradas de estos cuadros de texto aparecen en el archivo .rc marcadas por `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, y `TEXTINCLUDE 3` respectivamente. Para obtener más información, consulte [TN035: Usar varios archivos de recursos y archivos de encabezado con Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Una vez que se realizan cambios en el archivo de recursos mediante el **incluye recursos** cuadro de diálogo, debe cerrar y volver a abrir el archivo .rc para que los cambios surtan efecto.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Para incluir recursos en el proyecto en tiempo de compilación

1. Sitúe los recursos en un archivo de script de recursos con un nombre de archivo único. No use *projectname*.rc, ya que esto es el nombre del archivo usado para el archivo de script de recursos principal.

1. Haga clic en el archivo .rc en [vista de recursos](../windows/resource-view-window.md) y elija **incluye recursos** en el menú contextual.

1. En el **Rectivas de tiempo** , agregue el [#include](../preprocessor/hash-include-directive-c-cpp.md) directiva de compilador para incluir el nuevo archivo de recursos en el archivo de recursos principal en el entorno de desarrollo.

   Los recursos en los archivos incluidos de esta manera solo se convierten en parte del archivo ejecutable en tiempo de compilación y no están disponibles para edición o modificación cuando se trabaja en el archivo .rc principal de su proyecto. Los archivos .rc incluidos deben estar abiertos por separado y los archivos incluidos sin la extensión .rc no se puede editables los editores de recursos.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Para especificar directorios de inclusión para un recurso específico (archivo .rc)

1. Haga clic en el archivo .rc en **el Explorador de soluciones** y seleccione **propiedades**.

1. Seleccione el **recursos** nodo en el panel izquierdo y especifique cualquier adicionales incluyen directorios en el **directorios de inclusión adicionales** propiedad.

### <a name="to-find-symbols-in-resources"></a>Para buscar símbolos en recursos:

1. Vaya al menú **editar** > [Buscar símbolo](/visualstudio/ide/go-to).

   > [!TIP]
   > Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) en la búsqueda, seleccione [buscar en archivos](/visualstudio/ide/reference/find-command) en el **editar** menú en lugar de **Buscar símbolo**. Seleccione el **uso: Las expresiones regulares** casilla de verificación en la [cuadro de diálogo Buscar](/visualstudio/ide/finding-and-replacing-text) y en el **Find What** cuadro puede elegir una expresión regular de búsqueda en la lista desplegable. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro.

1. En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba la tecla de aceleración que desea buscar (por ejemplo, `ID_ACCEL1`).

1. Seleccione cualquiera de los **buscar** opciones y elegir **Buscar siguiente**.

> [!NOTE]
> No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: Crear recursos](../windows/how-to-create-a-resource-script-file.md)<br/>
[Cómo: Administrar recursos](../windows/how-to-copy-resources.md)<br/>