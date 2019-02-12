---
title: Filtrar Incluir recursos en tiempo de compilación (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 8df5a8ee6583b1e9f5c50a428b69babb0d56961b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152383"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Filtrar Incluir recursos en tiempo de compilación (C++)

Normalmente, es fácil y cómoda para trabajar con la organización predeterminada de todos los recursos en un archivo de recursos (.rc) de la secuencia de comandos. Sin embargo, puede agregar recursos de otros archivos al proyecto actual en tiempo de compilación enumerándolos en el **Rectivas de tiempo** cuadro el **incluye recursos** cuadro de diálogo.

Hay varias razones para incluir recursos en un archivo distinto del archivo .rc principal:

- Para agregar comentarios a instrucciones de recursos que no se eliminan al guardar el archivo .rc.

   Los editores de recursos no leen directamente .rc o `resource.h` archivos. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como el proceso de compilación con una normal, se descarta la información que no es simbólica (por ejemplo, los comentarios) durante el proceso de compilación. Cada vez que el archivo .aps obtiene fuera de sincronización con el archivo .rc, se vuelve a generar el archivo .rc (por ejemplo, cuando se guarda, el editor de recursos sobrescribe el archivo .rc y `resource.h` archivo). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc.

- Para incluir recursos que ya se ha desarrollado y probado y no necesitan modificación. (Los archivos que se incluyen, pero no tienen una extensión .rc no ser editables por los editores de recursos).

- Para incluir recursos que se usan en proyectos diferentes o que forman parte de un sistema de control de versiones de código fuente y, por lo tanto, debe existir en una ubicación central donde las modificaciones afectarán a todos los proyectos.

- Para incluir recursos (por ejemplo, recursos RCDATA) que se encuentran en un formato personalizado. Los recursos RCDATA podrían tener requisitos especiales. Por ejemplo, no se puede utilizar una expresión como un valor del campo nameID. Para más información, consulte la documentación de Windows SDK.

Si tiene secciones en los archivos .rc que cumplen alguna de estas condiciones, debe colocar las secciones en uno o varios archivos .rc independientes e incluyen en el proyecto con el **incluye recursos** cuadro de diálogo. El *Projectname*archivo. RC2 creado en el subdirectorio \res de un proyecto nuevo se usa para este propósito.

Puede usar el **incluye recursos** cuadro de diálogo en un proyecto de C++ para modificar trabajo habitual del entorno de almacenamiento de todos los recursos en el archivo .rc del proyecto y todos [símbolos](../windows/symbols-resource-identifiers.md) en Resource.h.

Para abrir el **incluye recursos** de archivos en el cuadro de diálogo, haga una .rc [vista de recursos](../windows/resource-view-window.md), a continuación, elija **incluye recursos** en el menú contextual. Este cuadro de diálogo tiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Archivo de encabezado de símbolos**|Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de los símbolos del archivo de recursos. Para obtener más información, consulte [cambiar los archivos de encabezado de los nombres de símbolos](../windows/changing-the-names-of-symbol-header-files.md).|
|**Directivas de símbolos de solo lectura**|Permite incluir archivos de encabezado que contienen los símbolos que no deberían modificarse durante una sesión de edición. Por ejemplo, se puede incluir un archivo de símbolos compartido por varios proyectos. También se pueden incluir archivos .h de MFC. Para obtener más información, consulte [símbolos incluidos compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).|
|**Directivas de tiempo de compilación**|Permite incluir archivos de recursos creados y editados con independencia de los recursos en el archivo principal de recursos, contienen las directivas de tiempo de compilación (por ejemplo, las directivas que se incluyen de forma condicional recursos), o los recursos en un formato personalizado. También puede usar el **cuadro directivas de tiempo de compilación** para incluir archivos de recursos MFC estándares. Para obtener más información, consulte [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).|

> [!NOTE]
> Las entradas de estos cuadros de texto aparecen en el archivo .rc marcadas por `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, y `TEXTINCLUDE 3` respectivamente. Para obtener más información, consulte [TN035: Usar varios archivos de recursos y archivos de encabezado con Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Una vez que se ha realizado cambios en el archivo de recursos mediante el **incluye recursos** cuadro de diálogo, deberá cerrar el archivo .rc y vuelva a abrirlo para que los cambios surtan efecto.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en la Guía del desarrollador de .NET Framework.

## <a name="to-include-resources-in-your-project-at-compile-time"></a>Para incluir recursos en el proyecto en tiempo de compilación

1. Sitúe los recursos en un archivo de script de recursos con un nombre de archivo único. No use *projectname*.rc, porque este nombre es el nombre de archivo usado para el archivo de script de recursos principal.

1. Haga clic en el archivo .rc (en [vista de recursos](../windows/resource-view-window.md)) y elija **incluye recursos** en el menú contextual.

1. En el **Rectivas de tiempo** , agregue el [#include](../preprocessor/hash-include-directive-c-cpp.md) directiva de compilador para incluir el nuevo archivo de recursos en el archivo de recursos principal en el entorno de desarrollo.

   Los recursos de los archivos incluidos de esta manera pasan a formar parte del archivo ejecutable en tiempo de compilación. No están directamente disponibles para la edición o modificación cuando se trabaja en el archivo .rc principal de su proyecto. Abra los archivos .rc incluidos por separado. Los archivos que se incluyen, pero no tienen una extensión .rc no ser editables por los editores de recursos.

## <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Para especificar directorios de inclusión para un recurso específico (archivo .rc)

1. Haga clic en el archivo .rc en el Explorador de soluciones y seleccione **propiedades** en el menú contextual.

1. En el **páginas de propiedades** cuadro de diálogo, seleccione el **recursos** nodo en el panel izquierdo, a continuación, especifique el adicionales incluyen directorios en el **directoriosdeinclusiónadicionales**propiedad.

## <a name="to-find-symbols-in-resources"></a>Para buscar símbolos en recursos:

1. Desde el **editar** menú, elija **Buscar símbolo**.

1. En el [cuadro de diálogo Buscar símbolo](/visualstudio/ide/go-to), en el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba la tecla de aceleración que desea buscar (por ejemplo, ID_ACCEL1).

   > [!TIP]
   > Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) para la búsqueda, debe usar el [comando Buscar en archivos](/visualstudio/ide/reference/find-command) desde el **editar** menú en lugar de la **Buscar símbolo**comando. Para habilitar las expresiones regulares, debe tener el **uso: Las expresiones regulares** casilla seleccionada en el [cuadro de diálogo Buscar](/visualstudio/ide/finding-and-replacing-text). Después, puede seleccionar el botón de flecha derecha situada a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro.

1. Seleccione cualquiera de los **buscar** opciones.

1. Elija **Buscar siguiente**.

> [!NOTE]
> No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)<br/>