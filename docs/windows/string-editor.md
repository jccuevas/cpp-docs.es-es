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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370238"
---
# <a name="string-editor-c"></a>Editor de cadenas (C++)

Una tabla de cadenas es un recurso de Windows que contiene una lista de id., valores y títulos para todas las cadenas de su aplicación. Por ejemplo, los mensajes de la barra de estado se encuentran en la tabla de cadenas.

Al desarrollar una aplicación, puede tener varias tablas de cadenas: una para cada idioma o condición. Sin embargo, un módulo ejecutable solo tiene una tabla de cadenas. Una aplicación en ejecución puede hacer referencia a varias tablas de cadenas si coloca las tablas en varias DLL diferentes.

Las tablas de cadenas facilitan la localización de la aplicación en diferentes idiomas. Si todas las cadenas se encuentran en una tabla de cadenas, puede localizar la aplicación mediante la traducción de las cadenas (y otros recursos) sin cambiar el código fuente. Esta situación es más deseable que buscar y reemplazar manualmente varias cadenas en archivos de origen.

> [!NOTE]
> Windows no permite la creación de tablas de cadenas vacías. Si crea una tabla de cadenas sin entradas, se elimina automáticamente al guardar el archivo de recursos.

## <a name="how-to"></a>Procedimientos

El **Editor de cadenas** le permite:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Para buscar un recurso de cadena en la tabla de cadenas

1. Abra la tabla de cadenas haciendo doble clic en su icono en [la vista de](how-to-create-a-resource-script-file.md#create-resources)recursos .

1. Vaya al menú **Editar buscar** > **y reemplazar** y elija **Buscar**.

1. En el cuadro **Buscar,** seleccione una cadena de búsqueda anterior de la lista desplegable o escriba el texto del título o el identificador de recurso de la cadena que desea buscar.

1. Seleccione cualquiera de las opciones **Buscar** y seleccione **Buscar siguiente**.

> [!TIP]
> Para utilizar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) al buscar archivos, utilice el comando **Buscar en archivos** del menú **Editar.**
>
> Escriba una expresión regular para que coincida con un patrón o seleccione el botón situado a la derecha del cuadro **Buscar** para mostrar una lista de expresiones de búsqueda regulares. Al seleccionar una expresión de esta lista, se sustituye como texto de búsqueda en el cuadro **Buscar.**
>
> Si utiliza expresiones regulares, asegúrese de que la casilla **Usar: Expresiones regulares** esté activada.

### <a name="to-add-or-delete-a-string-resource"></a>Para agregar o eliminar un recurso de cadena

Puede insertar o eliminar rápidamente entradas en la tabla de cadenas mediante el Editor de **cadenas**. Las nuevas cadenas se colocan al final de la tabla y se les da el siguiente identificador disponible. Puede editar las propiedades **ID**, **Value**o **Caption** en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) según sea necesario.

El Editor de **cadenas** se asegura de que no use un identificador que ya esté en uso. Si selecciona un ID ya en uso, el **Editor** de cadenas le `IDS_STRING58113`notificará y, a continuación, asignará un identificador único genérico, por ejemplo.

#### <a name="to-add-a-string-table-entry"></a>Para agregar una entrada de tabla de cadenas

1. Abra la tabla de cadenas haciendo doble clic en su icono en [la vista de](how-to-create-a-resource-script-file.md#create-resources)recursos .

1. Haga clic con el botón derecho en la tabla de cadenas y elija **Nueva cadena**.

1. En el Editor de **cadenas**, seleccione un **identificador** en la lista desplegable **ID** o escriba un *ID* directamente en su lugar.

1. Edite el **valor**, si es necesario.

1. Escriba una entrada para el **título**.

   > [!NOTE]
   > Las cadenas nulas no están permitidas en las tablas de cadenas de Windows. Si crea una entrada en la tabla de cadenas que es una cadena nula, recibirá un mensaje pidiéndole que **escriba una cadena para esta entrada**de tabla .

#### <a name="to-delete-a-string-table-entry"></a>Para eliminar una entrada de tabla de cadenas

Seleccione la entrada que desea eliminar y realice una de las siguientes acciones:

- Vaya al menú **Editar** > **eliminar**.

- Haga clic con el botón derecho en la cadena que desea eliminar y elija **Delete**.

- Pulse la tecla **Suprimir.**

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Para mover una cadena de un archivo de script de recursos a otro

1. [Abra las tablas](../windows/how-to-create-a-resource-script-file.md)de cadenas en ambos archivos .rc .

1. Haga clic con el botón derecho en la cadena que desea mover y elija **Cortar**.

1. Coloque el cursor en la ventana editor de **cadenas** de destino.

1. En el archivo *.rc* al que desea mover la cadena, haga clic con el botón derecho y elija **Pegar**.

> [!NOTE]
> Si el **identificador** o el **valor** de la cadena movida entran en conflicto con un **identificador** o **valor** existente en el archivo de destino, cambie ese **identificador** o el **valor** de la cadena movida.

### <a name="to-change-the-properties-of-a-string-resource"></a>Para cambiar las propiedades de un recurso de cadena

Puede utilizar la edición in situ para cambiar las propiedades **ID**, **Value**y **Caption.**

> [!NOTE]
> También puede editar las propiedades de una cadena en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Para cambiar una cadena o su identificador

1. Abra la tabla de cadenas haciendo doble clic en su icono en [la vista de](how-to-create-a-resource-script-file.md#create-resources)recursos .

1. Seleccione la cadena que desea editar y haga doble clic en la columna **ID**, **Valor**o **Título,** a continuación, puede:

   - Seleccione un **ID** en la lista desplegable **ID** o escriba un *ID* directamente en su lugar.

   - Escriba un número diferente en la columna **Valor.**

   - Escriba edits en la columna **Subtítulo.**

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Para cambiar la propiedad caption de varios recursos de cadena

1. Abra la tabla de cadenas haciendo doble clic en su icono en [la vista de](how-to-create-a-resource-script-file.md#create-resources)recursos .

1. Seleccione las cadenas que desea cambiar manteniendo presionada la **tecla Ctrl** mientras selecciona cada una.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba un nuevo valor para la propiedad que desea cambiar.

1. Presione **Entrar**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Para agregar formato o caracteres especiales a un recurso de cadena

1. Abra la tabla de cadenas haciendo doble clic en su icono en [la vista de](how-to-create-a-resource-script-file.md#create-resources)recursos .

1. Seleccione la cadena que desea modificar.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue cualquiera de las secuencias de escape estándar enumeradas a continuación al texto del cuadro **Subtítulo** y pulse **Intro**.

   |Para conseguir esto...|Escriba este...|
   |-----------------|---------------|
   | Línea nueva | \\n |
   | Retorno de carro | \\R |
   | Pestaña | \\t |
   | Barra diagonal inversa (\\) | \\\\ |
   | Carácter ASCII | \\ddd (notación octal) |
   | Alerta (campana) | \\a |

   > [!NOTE]
   > El Editor de **cadenas** no admite el conjunto completo de caracteres ASCI con escape. Solo puede utilizar los mencionados anteriormente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Cadenas de editores](../windows/resource-editors.md)
[Strings](/windows/win32/menurc/strings) de recursos<br/>
[Acerca de las cadenas](/windows/win32/menurc/about-strings)<br/>
[Personalizar los diseños de ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
