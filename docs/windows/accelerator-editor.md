---
title: Editor de aceleradores (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: 5ece5c7e85a3ef59b728474746e9553a751d43c6
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226350"
---
# <a name="accelerator-editor-c"></a>Editor de aceleradores (C++)

Una tabla de aceleradores es un recurso de Windows de C++ que contiene una lista de teclas de aceleración (también conocido como teclas de método abreviado) y los identificadores de comandos que están asociados con ellas. Un programa puede tener más de una tabla de aceleradores.

Normalmente, los aceleradores se usan como métodos abreviados de teclado para comandos de programa que también están disponibles en un menú o una barra de herramientas. Sin embargo, puede usar la tabla de aceleradores para definir las combinaciones de teclas para los comandos que no tienen asociado un objeto de interfaz de usuario.

Puede usar la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para enlazar comandos de teclas de aceleración al código.

Para obtener una lista de teclas de aceleración predefinidas, vea [teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md).

   > [!TIP]
   > Al usar el **acelerador** editor, hacer clic en para mostrar un menú contextual de comandos usados con frecuencia. Los comandos disponibles dependen del objeto al que apunta el puntero.

   > [!NOTE]
   > Windows no permite crear tablas de aceleradores vacías. Si crea una tabla de aceleradores sin entradas, se elimina automáticamente al guardar la tabla.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="accelerator-properties"></a>Propiedades de Acelerador

Puede establecer propiedades de acelerador el [ventana propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede usar el **acelerador** editor para modificar las propiedades de Acelerador de la tabla de aceleradores. Los cambios realizados mediante el **propiedades** ventana o el **acelerador** editor tiene el mismo resultado: las modificaciones se reflejan inmediatamente en la tabla de aceleradores.

### <a name="id-property"></a>ID (propiedad)

El **ID** propiedad hace referencia a cada entrada de la tabla de aceleradores en código de programa. Esta entrada es el valor del comando que va a recibir el programa cuando un usuario presiona la tecla de aceleración o una combinación de teclas. Para realizar un acelerador igual que un elemento de menú, realice sus identificadores de la misma (siempre y cuando el identificador de la tabla de aceleradores es el mismo que el identificador para el recurso de menú).

Hay tres propiedades para cada Id. de acelerador: el **modificador** propiedad, el **clave** propiedad y el **tipo** propiedad.

#### <a name="modifier-property"></a>Modifier (propiedad)

El **modificador** propiedad establece el control de combinaciones de teclas para el acelerador.

> [!NOTE]
> En el **propiedades** ventana, esta propiedad aparece como tres independiente **booleano** propiedades, que puede controlarse de forma independiente: **ALT**, **Ctrl**, y **MAYÚS**.

Los siguientes son entradas legales para el **modificador** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |**Ninguno**|Usuario presiona sólo el **clave** valor. Este valor se utiliza la forma más eficaz con los valores ASCII/ANSI 001 a 026, que se interpreta como ^ A ^ Z (**CTRL+a** a través de **CTRL+z**).|
   |**Alt**|El usuario debe presionar el **Alt** clave antes de la **clave** valor.|
   |**Ctrl**|El usuario debe presionar el **Ctrl** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**Mayús**|El usuario debe presionar el **MAYÚS** clave antes de la **clave** valor.|
   |**Ctrl+Alt**|El usuario debe presionar el **Ctrl** clave y el **Alt** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**CTRL + MAYÚS**|El usuario debe presionar el **Ctrl** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**ALT + MAYÚS**|El usuario debe presionar el **Alt** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**Ctrl + Alt + Mayús**|El usuario debe presionar **Ctrl**, **Alt**, y **MAYÚS** antes de la **clave** valor. No es válido con el tipo de ASCII.|

#### <a name="key-property"></a>Key (propiedad)

El **clave** propiedad establece la clave real que se usará como el acelerador.

Los siguientes son entradas legales para el **clave** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |Un entero entre 0 y 255 en formato decimal.|El valor determina si el valor se trata como ASCII o ANSI como sigue:<br/><br/>-Números de dígito siempre se interpretan como la clave correspondiente, en lugar de como valores ASCII o ANSI.<br/>-Los valores de 1 a 26, si van precedidos de ceros, se interpretan como ^ A ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presiona con la **Ctrl** clave se mantiene presionada.<br/>-Valores 27-32 siempre se interpretan como valores de tres dígitos decimales comprendidos entre 032 027.<br/>-Los valores de 033 a 255, ya sea precedido de 0 o no se interpretan como valores ANSI.|
   |Un carácter único teclado.|Mayúscula A - Z o los números 0 - 9 pueden ser ASCII o valores de clave virtuales; cualquier otro carácter solo es ASCII.|
   |Un carácter único teclado en el intervalo A - Z (sólo mayúsculas), precedida por un símbolo de intercalación (^) (por ejemplo, ^ C).|Esta opción especifica el valor de ASCII de la clave cuando se presiona con la **Ctrl** tecla presionada.|
   |Cualquier identificador de clave virtual válido.|El cuadro de lista desplegable clave en la tabla de aceleradores contiene una lista de identificadores de clave virtuales estándares.|

> [!NOTE]
> Cuando escribe un valor ASCII, las opciones de la propiedad modificador son limitadas. La única clave de control disponible para su uso es la **Alt** clave.

> [!TIP]
> Es otra manera de definir una tecla de aceleración para el botón derecho en una o varias entradas en la tabla de aceleradores, elija **tecla siguiente** en el menú contextual y, a continuación, presione cualquiera de las claves o combinaciones de teclas del teclado. El **tecla siguiente** comando también está disponible desde el **editar** menú.

#### <a name="type-property"></a>Type (propiedad)

El **tipo** propiedad determina si la combinación de teclas de método abreviado asociada con el Id. de acelerador se interpreta como un valor de clave ASCII/ANSI o una combinación de tecla virtual (VIRTKEY).

- Si el **tipo** propiedad es ASCII, el **modificador** sólo puede ser propiedad `None` o `Alt`, o puede tener un acelerador que usa el **Ctrl** clave () anteponer a la clave con un `^`).

- Si el **tipo** propiedad es VIRTKEY, cualquier combinación de `Modifier` y `Key` valores es válido.

> [!NOTE]
> Si desea especificar un valor en la tabla de aceleradores y tienen el valor se tratan como ASCII/ANSI, simplemente haga clic en el **tipo** para la entrada en la tabla y seleccione ASCII en la lista desplegable. Sin embargo, si usa el **tecla siguiente** comando (**editar** menú) para especificar el `Key`, debe cambiar la **tipo** propiedad de VIRTKEY a ASCII *antes* escribir el `Key` código.

## <a name="accelerator-tables"></a>Tablas de aceleradores

En un proyecto de C++, puede editar una tabla de aceleradores directamente con la edición en contexto en el **acelerador** editor.

Los procedimientos siguientes hacen referencia al uso de páginas de propiedades estándar, sin embargo, tanto la edición en contexto y el método de página de propiedad tienen el mismo resultado. Los cambios realizados mediante las páginas de propiedades o mediante la edición en contexto se reflejan inmediatamente en la tabla de aceleradores.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

### <a name="to-edit-in-an-accelerator-table"></a>Para editar el contenido de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione una entrada en la tabla y seleccione esta opción para activar la edición en contexto.

1. Seleccione en el cuadro combinado desplegable o escriba para realizar cambios.

   - Para **ID**, seleccione en la lista o escriba para editar.

   - Para **modificador**, seleccione en la lista.

   - Para **clave**, seleccione en la lista o escriba para editar.

   - Para **tipo**, seleccione **ASCII** o **VIRTKEY** en la lista.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Para buscar una entrada en una tabla de aceleradores abierta:

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione un encabezado de columna para ordenar el contenido de la columna alfabéticamente. Por ejemplo, seleccione **ID** para mostrar alfabéticamente todos los identificadores de la tabla de aceleradores.

A continuación, puede examinar la lista y buscar la entrada.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Haga doble clic en la tabla de aceleradores y elija **nuevo acelerador** desde el menú contextual, o seleccione la entrada de fila vacía en la parte inferior de la tabla.

1. Seleccione un **Id. de** en la lista desplegable en el Id. de cuadro o escriba un nuevo identificador en el **ID** cuadro.

1. Tipo de la **clave** que desea usar como acelerador o contextual y elija **tecla siguiente** en el menú contextual para establecer una combinación de teclas (el **tecla siguiente** comando es También está disponible en el **editar** menú).

1. Cambiar el **modificador** y **tipo**, si es necesario.

1. Presione **ENTRAR**.

   > [!NOTE]
   > Asegúrese de que todos los aceleradores que defina sean únicos. Puede tener varias combinaciones de teclas asignadas al mismo identificador no tiene ningún efecto negativos, por ejemplo, **Ctrl** + **P** y **F8** pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien, por ejemplo, **Ctrl** + **Z** asignado a tanto a ID_SPELL_CHECK como a ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Para eliminar una entrada de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la entrada que quiera eliminar. (Mantenga presionada la **Ctrl** o **MAYÚS** clave durante la selección para elegir varias entradas.)

1. Haga clic en y elija **eliminar** en el menú contextual (o seleccione **eliminar** desde el **editar** menú).

> [!TIP]
> Un acceso directo para su eliminación consiste en presionar el **eliminar** clave.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Para mover o copiar una entrada de una tabla de aceleradores a otro archivo de script de recursos

1. Abra las tablas de aceleradores en los dos archivos de script de recursos.

1. Seleccione la entrada que desea mover.

1. Desde el **editar** menú, elija **copia** o **cortar**.

1. Seleccione una entrada en el archivo de script de recursos de destino.

1. Desde el **editar** menú, elija **pegar**.

   > [!NOTE]
   > También puede usar las teclas de método abreviado para copiar y pegar.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para cambiar las propiedades de varias teclas de aceleración

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione las teclas de aceleración que desee cambiar, mantenga presionada la **Ctrl** clave mientras selecciona cada uno de ellos.

1. Vaya a la [ventana propiedades](/visualstudio/ide/reference/properties-window) y escriba los valores que desea que todos los aceleradores seleccionados para compartir.

   > [!NOTE]
   > Cada valor de modificador aparece como una propiedad booleana en el **propiedades** ventana. Si cambia un [modificador](../windows/accelerator-modifier-property.md) valor en el **propiedades** ventana, la tabla de aceleradores tratará al nuevo modificador como una adición a los modificadores que previamente contenía. Por este motivo, si establece los valores de modificador, deberá establecer todos ellos para asegurarse de que todos los aceleradores compartan la misma **modificador** configuración.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)

[Edición en una tabla de aceleradores](../windows/editing-in-an-accelerator-table.md)<br/>
[Teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)<br/>