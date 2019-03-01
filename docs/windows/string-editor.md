---
title: Editor de cadenas (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: d040c09b36c2b46036744c8a263802da48cd8e60
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210801"
---
# <a name="string-editor-c"></a>Editor de cadenas (C++)

Una tabla de cadenas es un recurso de Windows que contiene una lista de id., valores y títulos para todas las cadenas de su aplicación. Por ejemplo, los mensajes de la barra de estado se encuentran en la tabla de cadenas.

Al desarrollar una aplicación, puede tener varias tablas de cadenas: una para cada idioma o condición. Sin embargo, un módulo ejecutable solo tiene una tabla de cadenas. Una aplicación en ejecución puede hacer referencia a varias tablas de cadenas si coloca las tablas en varias DLL diferentes.

Las tablas de cadenas facilitan la localización de la aplicación en diferentes idiomas. Si todas las cadenas se encuentran en una tabla de cadenas, puede localizar la aplicación mediante la traducción de las cadenas (y otros recursos) sin cambiar el código fuente. Esta situación es más deseable que buscar y reemplazar las distintas cadenas en archivos de origen manualmente.

> [!NOTE]
> Windows no permiten la creación de tablas de una cadena vacía. Si crea una tabla de cadenas sin entradas, se elimina automáticamente al guardar el archivo de recursos.

## <a name="how-to"></a>Procedimientos

El **Editor de cadenas** le permite:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Para buscar un recurso de cadena en la tabla de cadenas

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Vaya al menú **editar** > **buscar y reemplazar** y elija **encontrar**.

1. En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba el título texto o identificador de recurso de la cadena que desea buscar.

1. Seleccione cualquiera de los **buscar** opciones y seleccione **Buscar siguiente**.

> [!TIP]
> Para usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) al buscar archivos, utilice el **buscar en archivos** comando en el **editar** menú.
>
> Escriba una expresión regular para coincidir con un patrón o seleccione el botón a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro.
>
> Si utiliza expresiones regulares, asegúrese del **usar: Las expresiones regulares** casilla está activada.

### <a name="to-add-or-delete-a-string-resource"></a>Para agregar o eliminar un recurso de cadena

Rápidamente puede insertar o eliminar las entradas en la tabla de la cadena mediante la **Editor de cadenas**. Nuevas cadenas se colocan al final de la tabla y reciben el siguiente identificador disponible. Puede editar el **ID**, **valor**, o **título** propiedades en el [ventana propiedades](/visualstudio/ide/reference/properties-window) según sea necesario.

El **Editor de cadenas** se asegura de que no use un identificador que ya está en uso. Si selecciona un identificador ya en uso, el **Editor de cadenas** le notificaremos y, a continuación, asignar un identificador genérico único, por ejemplo `IDS_STRING58113`.

Para agregar una entrada de tabla de cadenas:

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Haga doble clic en la tabla de cadenas y elija **nueva cadena**.

1. En el **Editor de cadenas**, seleccione un **Id. de** desde el **Id. de** lista desplegable o escriba un *ID* directamente en su lugar.

1. Editar el **valor**, si es necesario.

1. Escriba una entrada para el **título**.

   > [!NOTE]
   > No se permiten cadenas nulas en las tablas de cadenas de Windows. Si crea una entrada en la tabla de cadenas es una cadena nula, recibirá un mensaje que le pide que **escriba una cadena para esta entrada de tabla**.

Para eliminar una entrada de tabla de cadenas:

Seleccione la entrada que desea eliminar y realice una de las siguientes acciones:

- Vaya al menú **editar** > **eliminar**.

- Haga clic en la cadena para eliminar y elija **eliminar**.

- Presione el **eliminar** clave.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Para mover una cadena de archivo de script de un recurso a otro

1. [Abra las tablas de cadenas en los dos archivos .rc](../windows/how-to-create-a-resource-script-file.md).

1. Haga clic en la cadena para mover y elija **cortar**.

1. Coloque el cursor en el destino **Editor de cadenas** ventana.

1. En el archivo .rc en la que desea mover la cadena, haga clic en y elija **pegar**.

> [!NOTE]
> Si el **ID** o **valor** de conflictos con una cadena desplazada **ID** o **valor** en el archivo de destino, ya sea que **ID** o **valor** de los cambios de la cadena desplazada.

### <a name="to-change-the-properties-of-a-string-resource"></a>Para cambiar las propiedades de un recurso de cadena

Puede usar la edición en contexto para cambiar la **ID**, **valor**, y **título** propiedades.

> [!NOTE]
>  También puede editar propiedades de una cadena en el [ventana propiedades](/visualstudio/ide/reference/properties-window).

Para cambiar una cadena o su identificador:

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la cadena que desea editar y haga doble clic en el **ID**, **valor**, o **título** columna, puede realizar:

   - Seleccione un **Id. de** desde el **Id. de** lista desplegable o escriba un *ID* directamente en su lugar.

   - Escriba un número diferente de la **valor** columna.

   - Escriba las modificaciones en el **título** columna.

Para cambiar la propiedad caption de varios recursos de cadena:

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione las cadenas que desee cambiar, mantenga presionada la **Ctrl** clave mientras selecciona cada uno de ellos.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba un nuevo valor para la propiedad que desee cambiar.

1. Presione **ENTRAR**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Para agregar formato o caracteres especiales a un recurso de cadena

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la cadena que desea modificar.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), agregue cualquiera de las secuencias de escape estándar enumerados a continuación para el texto en el **título** cuadro y presione **ENTRAR**.

   |Para obtener esto...|Escriba lo siguiente...|
   |-----------------|---------------|
   | Nueva línea | \\n |
   | Retorno de carro | \\r |
   | Tab | \\t |
   | Barra diagonal inversa (\\) | \\\\ |
   | Carácter ASCII | \\ddd (notación octal) |
   | alerta (campana) | \\a |

   > [!NOTE]
   > El **Editor de cadenas** no es compatible con el conjunto completo de caracteres ASCII con escape. Solo se pueden usarlos mencionados anteriormente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->