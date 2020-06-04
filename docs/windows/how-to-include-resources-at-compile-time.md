---
title: 'Cómo: incluir recursos en tiempo de compilación (C++)'
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
ms.openlocfilehash: e931a0246340e81049df6ed0f8e26a4b91b570c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215202"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Cómo: incluir recursos en tiempo de compilación (C++)

De forma predeterminada, todos los recursos se encuentran en un archivo de script de recursos (. RC), sin embargo, hay muchas razones para colocar recursos en un archivo distinto del archivo. RC principal:

- Para agregar comentarios a instrucciones de recursos que no se eliminarán cuando guarde el archivo. rc.

- Para incluir recursos que ya se han desarrollado y probado, y que no necesitan más modificaciones. Los editores de recursos no podrán editar los archivos incluidos pero que no tengan una extensión. rc.

- Para incluir recursos que se usan en proyectos diferentes o que forman parte de un sistema de control de versiones de código fuente. Estos recursos deben existir en una ubicación central en la que las modificaciones afecten a todos los proyectos.

- Para incluir recursos (como recursos RCDATA) que tengan un formato personalizado. Los recursos RCDATA tienen requisitos especiales en los que no se puede usar una expresión como valor para el campo `nameID`.

Si tiene secciones en los archivos. RC existentes que cumplen cualquiera de estas condiciones, coloque estas secciones en uno o varios archivos. RC independientes e inclúyalo en el proyecto mediante el cuadro de diálogo archivos de **inclusión de recursos** .

## <a name="resource-includes"></a>Inclusión de recursos

Puede agregar recursos de otros archivos al proyecto en tiempo de compilación si los enumera en el cuadro **directivas de tiempo de compilación** del cuadro de diálogo archivos de **inclusión de recursos** . Utilice el cuadro de diálogo archivos de **inclusión de recursos** para modificar la disposición de trabajo normal del entorno del proyecto de almacenamiento de todos los recursos en el archivo Project. RC y en todos los [símbolos](../windows/symbols-resource-identifiers.md) de `Resource.h`.

Para empezar, abra el cuadro de diálogo archivos de **inclusión de recursos** . para ello, haga clic con el botón secundario en un archivo. rc en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), seleccione **inclusión de recursos** y tenga en cuenta las siguientes propiedades:

| Propiedad | Descripción |
|---|---|
| **Archivo de encabezado de símbolos** | Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de símbolos para los archivos de recursos.<br/><br/>Para obtener más información, vea [cambiar los nombres de los archivos de encabezado de símbolos](../windows/changing-the-names-of-symbol-header-files.md). |
| **Directivas de símbolos de solo lectura** | Permite incluir archivos de encabezado que contienen símbolos que no se deben modificar.<br/><br/>Por ejemplo, archivos de símbolos que se van a compartir con otros proyectos. Esto también puede incluir archivos. h de MFC. Para obtener más información, vea [incluir símbolos compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Directivas de tiempo de compilación** | Permite incluir archivos de recursos que se crean y editan por separado de los recursos del archivo de recursos principal, que contienen directivas de tiempo de compilación (como las directivas que incluyen recursos condicionalmente) o contienen recursos en un formato personalizado.<br/><br/>También puede usar el **cuadro directivas de tiempo de compilación** para incluir archivos de recursos de MFC estándar. |

> [!NOTE]
> Las entradas de estos cuadros de texto aparecen en el archivo. RC marcado por `TEXTINCLUDE 1`, `TEXTINCLUDE 2`y `TEXTINCLUDE 3` respectivamente. Para obtener más información, vea [TN035: usar varios archivos de recursos y archivos de C++encabezado con Visual ](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Una vez realizados los cambios en el archivo de recursos mediante el cuadro de diálogo archivos de **inclusión de recursos** , debe cerrar y volver a abrir el archivo *. RC* para que los cambios surtan efecto.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Para incluir recursos en el proyecto en tiempo de compilación

1. Sitúe los recursos en un archivo de script de recursos con un nombre de archivo único. No use *projectname. RC*, ya que es el nombre del archivo que se usa para el archivo de script de recursos principal.

1. Haga clic con el botón secundario en el archivo *. RC* en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) y seleccione **inclusiones de recursos**.

1. En el cuadro **directivas de tiempo de compilación** , agregue la Directiva de compilador [#include](../preprocessor/hash-include-directive-c-cpp.md) para incluir el nuevo archivo de recursos en el archivo de recursos principal del entorno de desarrollo.

Los recursos de los archivos incluidos de esta manera solo forman parte del archivo ejecutable en tiempo de compilación y no están disponibles para su edición o modificación cuando se trabaja en el archivo. RC principal del proyecto. Los archivos. RC incluidos deben abrirse por separado y los editores de recursos no podrán editar los archivos incluidos sin la extensión. rc.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Para especificar directorios de inclusión para un archivo de recursos (. RC) específico

1. Haga clic con el botón secundario en el archivo *. RC* en **Explorador de soluciones** y seleccione **propiedades**.

1. Seleccione el nodo **recursos** en el panel izquierdo y especifique los directorios de inclusión adicionales en la propiedad **directorios de inclusión adicionales** .

### <a name="to-find-symbols-in-resources"></a>Para buscar símbolos en recursos:

1. Vaya a menú **editar** > [Buscar símbolo](/visualstudio/ide/go-to).

   > [!TIP]
   > Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) en la búsqueda, seleccione [Buscar en archivos](/visualstudio/ide/reference/find-command) en el menú **edición** en lugar de **Buscar símbolo**. Active la casilla **usar expresiones regulares** en el cuadro de [diálogo Buscar](/visualstudio/ide/finding-and-replacing-text) y, en el cuadro **Buscar** , puede elegir una expresión de búsqueda normal en la lista desplegable. Al seleccionar una expresión de esta lista, se sustituye por el texto de búsqueda en el cuadro **Buscar** .

1. En el cuadro **Buscar** , seleccione una cadena de búsqueda anterior en la lista desplegable o escriba la tecla de aceleración que desea buscar, por ejemplo, `ID_ACCEL1`.

1. Seleccione cualquiera de las opciones de **búsqueda** y elija **Buscar siguiente**.

> [!NOTE]
> No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: crear recursos](../windows/how-to-create-a-resource-script-file.md)<br/>
[Cómo: administrar recursos](../windows/how-to-copy-resources.md)<br/>
