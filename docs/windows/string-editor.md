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
ms.openlocfilehash: 8f33ef6d0198f083e7cf1b1e1dc2129be9b3fab4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320567"
---
# <a name="string-editor-c"></a>Editor de cadenas (C++)

Una tabla de cadenas es un recurso de Windows que contiene una lista de id., valores y títulos para todas las cadenas de su aplicación. Por ejemplo, los mensajes de la barra de estado se encuentran en la tabla de cadenas.

Al desarrollar una aplicación, puede tener varias tablas de cadenas: una para cada idioma o condición. Sin embargo, un módulo ejecutable solo tiene una tabla de cadenas. Una aplicación en ejecución puede hacer referencia a varias tablas de cadenas si coloca las tablas en varias DLL diferentes.

Las tablas de cadenas facilitan la localización de la aplicación en diferentes idiomas. Si todas las cadenas se encuentran en una tabla de cadenas, puede localizar la aplicación mediante la traducción de las cadenas (y otros recursos) sin cambiar el código fuente. Esta situación es más deseable que buscar y reemplazar las distintas cadenas en archivos de origen manualmente.

## <a name="how-to"></a>Tema de procedimientos

Use la **cadena** editor para las siguientes acciones:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Para buscar un recurso de cadena en la tabla de cadenas

Puede buscar una o varias cadenas en la tabla de cadenas y usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) con el **buscar en archivos** comando (**editar** menú) para buscar todas las instancias de cadenas que coincide con un patrón.

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. En el **editar** menú, seleccione **buscar y reemplazar**, a continuación, elija **encontrar**.

1. En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba el título texto o identificador de recurso de la cadena que desea buscar.

1. Seleccione cualquiera de los **buscar** opciones.

1. Seleccione **Buscar siguiente**.

   > [!TIP]
   > Para usar expresiones regulares al buscar archivos, use el **buscar en archivos** comando. Escriba una expresión regular para coincidir con un patrón o seleccione el botón a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro. Si utiliza expresiones regulares, asegúrese del **usar: Las expresiones regulares** casilla está activada.

### <a name="to-add-or-delete-a-string-resource"></a>Para agregar o eliminar un recurso de cadena

Rápidamente puede insertar o eliminar las entradas en la tabla de la cadena mediante la **cadena** editor. Nuevas cadenas se colocan al final de la tabla y reciben el siguiente identificador disponible. Se puede editar el **ID**, **valor**, o **título** propiedades en el [ventana propiedades](/visualstudio/ide/reference/properties-window) según sea necesario.

El **cadena** editor garantiza que no use un identificador que ya está en uso. Si selecciona un identificador ya en uso, el **cadena** le notificaremos editor y, a continuación, asignar un identificador genérico único, por ejemplo `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Para agregar una entrada de tabla de cadenas

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Haga doble clic en la tabla de cadenas y elija **nueva cadena** en el menú contextual.

1. En el **cadena** editor, seleccione un **ID** en la lista de identificadores de lista desplegable o escriba directamente en un lugar de identificador.

1. Editar el **valor**, si es necesario.

1. Escriba una entrada para el **título**.

   > [!NOTE]
   > No se permiten cadenas nulas en las tablas de cadenas de Windows. Si crea una entrada en la tabla de cadenas es una cadena nula, recibirá un mensaje pidiéndole que "Especifique una cadena para esta entrada de tabla".

#### <a name="to-delete-a-string-table-entry"></a>Para eliminar una entrada de tabla de cadenas

Seleccione la entrada que quiera eliminar. Realice alguno de los siguientes procedimientos:

- En el **editar** menú, seleccione **eliminar**.

- Haga clic en la cadena que desea eliminar y elija **eliminar** en el menú contextual.

- Presione el **eliminar** clave.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Para mover una cadena de archivo de script de un recurso a otro

1. Abra las tablas de cadenas en los dos archivos .rc. (Para obtener más información, consulte [ver recursos en un archivo de Script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

1. Haga clic en la cadena que desea mover y elija **cortar** en el menú contextual.

1. Coloque el cursor en el destino **Editor de cadenas** ventana.

1. En el archivo .rc en la que desea mover la cadena, haga clic en y elija **pegar** en el menú contextual.

   > [!NOTE]
   > Si el **ID** o **valor** de conflictos con una cadena desplazada **ID** o **valor** en el archivo de destino, ya sea el **ID** o **valor** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **ID**, el **ID** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **valor**, **valor** de los cambios de la cadena desplazada.

### <a name="to-change-the-properties-of-a-string-resource"></a>Para cambiar las propiedades de un recurso de cadena

Puede usar la edición en contexto para cambiar el ID, value y propiedades de título.

#### <a name="to-change-a-string-or-its-identifier"></a>Para cambiar una cadena o su identificador.

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la cadena que desea editar y haga doble clic en el **ID**, **valor**, o **título** columna. Ahora hacer lo siguiente:

   - Seleccione un **ID** desde el **Id. de lista desplegable** lista o escriba un `ID` directamente en su lugar.

   - Escriba un número diferente de la **valor** columna.

   - Escriba las modificaciones en el **título** columna.

        > [!NOTE]
        >  También puede editar propiedades de una cadena en el [ventana propiedades](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Para cambiar la propiedad caption de varios recursos de cadena

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione las cadenas que desee cambiar, mantenga presionada la **Ctrl** clave mientras selecciona cada uno de ellos.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba un nuevo valor para la propiedad que desee cambiar.

1. Presione **ENTRAR**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Para agregar formato o caracteres especiales a un recurso de cadena

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la cadena que desea modificar.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), agregue cualquiera de las secuencias de escape estándar enumerados a continuación para el texto en el **título** cuadro y presione **ENTRAR**.

   |Para obtener esto|Escriba lo siguiente|
   |-----------------|---------------|
   | Nueva línea | \\n |
   | Retorno de carro | \\r |
   | Tab | \\t |
   | Barra diagonal inversa (\\) | \\\\ |
   | Carácter ASCII | \\ddd (notación octal) |
   | alerta (campana) | \\a |

> [!NOTE]
> El **cadena** editor no admite el conjunto completo de caracteres ASCII con escape. Solo se pueden usarlos mencionados anteriormente.

> [!NOTE]
> Windows no permite la creación de tablas de cadenas vacías. Si crea una tabla de cadenas sin entradas, se elimina automáticamente al guardar el archivo de recursos.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Cadenas](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[Acerca de las cadenas](/windows/desktop/menurc/about-strings)<br/>
[Personalizar los diseños de ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio)