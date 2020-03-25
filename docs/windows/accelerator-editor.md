---
title: Editor de aceleradores (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 80ef6cc9ec956d0041c4aa3fb6a6211868cc9d73
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167568"
---
# <a name="accelerator-editor-c"></a>Editor de aceleradores (C++)

Una tabla de aceleradores C++ es un recurso de Windows que contiene una lista de teclas de aceleración, conocidas como teclas de método abreviado, y los identificadores de comando asociados a ellas. Un programa puede tener más de una tabla de aceleradores.

Normalmente, los aceleradores se usan como métodos abreviados de teclado para comandos de programa que también están disponibles en un menú o una barra de herramientas. Sin embargo, puede usar la tabla de aceleradores para definir las combinaciones de teclas para los comandos que no tienen asociado un objeto de interfaz de usuario.

> [!TIP]
> Al usar el **Editor de aceleradores**, haga clic con el botón secundario para mostrar un menú contextual de comandos frecuentes. Los comandos disponibles dependen del objeto al que apunta el puntero.

Puede usar la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para enlazar comandos de teclas de aceleración al código. Para obtener una lista de teclas de aceleración predefinidas, vea [teclas de aceleración](../windows/predefined-accelerator-keys.md).

> [!NOTE]
> Windows no permite crear tablas de aceleradores vacías. Si crea una tabla de aceleradores sin entradas, se elimina automáticamente al guardar la tabla.

## <a name="accelerator-properties"></a>Propiedades de acelerador

Puede establecer propiedades de acelerador en el [ventana Propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede usar el **Editor de aceleradores** para modificar las propiedades de acelerador en la tabla de aceleradores. Los cambios realizados mediante la ventana **propiedades** o el **Editor de aceleradores** tienen el mismo resultado, las modificaciones se reflejan inmediatamente en la tabla de aceleradores.

La propiedad **ID** hace referencia a cada entrada de la tabla de aceleradores en el código del programa. Esta entrada es el valor de comando que el programa recibe cuando un usuario presiona la tecla de aceleración o una combinación de teclas. Para que un acelerador sea el mismo que un elemento de menú, haga que el **identificador** sea el mismo, siempre que el **identificador** de la tabla de aceleradores sea el mismo que el **identificador** del recurso de menú.

Cada **identificador** de acelerador tiene tres propiedades: **modificador**, **clave**y **tipo**

La propiedad **modificador** establece combinaciones de teclas de control para el acelerador.

> [!NOTE]
> En la ventana **propiedades** , la **propiedad modificador** aparece como tres propiedades **booleanas** independientes, que se pueden controlar de forma independiente: **Alt**, **Ctrl**y **MAYÚS**.

A continuación se indican entradas válidas para la propiedad **modificador** en la tabla de aceleradores:

   |Value|Descripción|
   |-----------|-----------------|
   |**None**|El usuario solo presiona el valor de **clave** .<br/><br/>Este valor se utiliza de forma más eficaz con los valores ASCII/ANSI 001 a través de 026, que se interpreta como ^ A a ^ Z (**Ctrl + a** a **Ctrl + Z**).|
   |**Alt**|El usuario debe presionar **Alt** antes del valor de la **clave** .|
   |**Ctrl**|El usuario debe presionar **Ctrl** antes del valor de **clave** , no válido con el tipo ASCII.|
   |**Mayús**|El usuario debe presionar la tecla **MAYÚS** antes del valor de **clave** .|
   |**Ctrl + Alt**|El usuario debe presionar **Ctrl** y **Alt** antes del valor de **clave** , no válido con el tipo ASCII.|
   |**Ctrl + Mayús**|El usuario debe presionar **Ctrl** y **MAYÚS** antes del valor de **clave** , no es válido con el tipo ASCII.|
   |**Alt + Mayús**|El usuario debe presionar **Alt** y **MAYÚS** antes del valor de **clave** , no válido con el tipo ASCII.|
   |**Ctrl + Alt + Mayús**|El usuario debe presionar **Ctrl**, **Alt**y **MAYÚS** antes del valor de **clave** , no válido con el tipo ASCII.|

La propiedad **clave** establece la clave real que se va a usar como acelerador.

A continuación se indican entradas válidas para la propiedad **clave** de la tabla de aceleradores:

   |Value|Descripción|
   |-----------|-----------------|
   |Entero comprendido entre 0 y 255 en formato decimal.|El valor determina si el valor se trata como ASCII o ANSI como se indica a continuación:<br/><br/>   -Los números de un solo dígito se interpretan siempre como la clave correspondiente, en lugar de como valores ASCII o ANSI.<br/>   -Los valores de 1 a 26, cuando están precedidos de ceros, se interpretan como ^ A a ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presiona con la tecla **Ctrl** presionada.<br/>   : Los valores de 27-32 se interpretan siempre como valores decimales de tres dígitos de 027 a 032.<br/>   : Los valores de 033 a 255, ya estén precedidos de 0 o no, se interpretan como valores ANSI.|
   |Un solo carácter de teclado.|Mayúsculas A-Z o los números 0-9 pueden ser valores ASCII o de clave virtual. Cualquier otro carácter es solo ASCII.|
   |Un solo carácter de teclado en el intervalo A-Z (solo en mayúsculas), precedido por un símbolo de intercalación (^), por ejemplo, ^ C.|Esta opción especifica el valor ASCII de la tecla cuando se presiona con la tecla **Ctrl** presionada.|
   |Cualquier identificador de clave virtual válido.|El cuadro **clave** desplegable de la tabla de aceleradores contiene una lista de identificadores de clave virtual estándar.|

> [!NOTE]
> Al escribir un valor ASCII, las opciones de la propiedad **modificador** son limitadas. La única tecla de control disponible para su uso es la tecla **Alt** .

> [!TIP]
> Un acceso directo para definir una tecla de aceleración consiste en hacer clic con el botón secundario en una entrada o en varias entradas de la tabla de aceleradores y, a continuación, elegir la **tecla siguiente** con el teclado.
>
> Este comando de **tecla con tipo siguiente** también está disponible en el menú **edición** .

La propiedad **Type** determina si la combinación de teclas de método abreviado asociada al **identificador** de acelerador se interpreta como un valor de clave ASCII/ANSI o una combinación de clave virtual (VIRTKEY).

- Si la propiedad **Type** es **ASCII**, la propiedad **modificadora** solo puede ser `None` o `Alt`, o bien puede tener un acelerador que use la tecla **Ctrl** , tal y como se especifica antes de la clave con una `^`.

- Si la propiedad **Type** es **VIRTKEY**, cualquier combinación de valores de **modificador** y **clave** es válida.

> [!NOTE]
> Si desea especificar un valor en la tabla de aceleradores y que el valor se trate como ASCII/ANSI, seleccione el **tipo** de la entrada en la tabla y seleccione **ASCII** en la lista desplegable. Sin embargo, si usa el **siguiente comando clave con tipo** en el **menú Edición** para especificar la **clave**, debe cambiar la propiedad **Type** de **VIRTKEY** a **ASCII** *antes* de escribir el código de **tecla** .

## <a name="accelerator-tables"></a>Tablas de aceleradores

En un C++ proyecto de, puede editar una tabla de aceleradores directamente con la edición en contexto en el **Editor de aceleradores**.

En los procedimientos siguientes se hace referencia al uso de páginas de propiedades estándar; sin embargo, la edición en contexto y el método de página de propiedades tienen el mismo resultado. Los cambios realizados mediante páginas de propiedades o mediante la edición en contexto se reflejan inmediatamente en la tabla de aceleradores.

### <a name="to-edit-in-an-accelerator-table"></a>Para editar el contenido de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Seleccione una entrada en la tabla y seleccione Activar la edición en contexto.

1. Seleccione en el cuadro combinado desplegable o escriba en su lugar para realizar cambios:

   - En **ID**, seleccione en la lista o escriba para editar.

   - En **modificador**, seleccione en la lista.

   - En **Key (clave**), seleccione en la lista o escriba para editar.

   - En **tipo**, seleccione **ASCII** o **VIRTKEY** en la lista.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Para buscar una entrada en una tabla de aceleradores abierta:

1. Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Seleccione un encabezado de columna para ordenar el contenido de la columna alfabéticamente. Por ejemplo, seleccione **ID** . para mostrar todos los identificadores de la tabla de aceleradores alfabéticamente.

   A continuación, puede examinar la lista y buscar la entrada.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Haga clic con el botón derecho en la tabla de aceleradores y elija **nuevo acelerador**, o bien seleccione la entrada de fila vacía en la parte inferior de la tabla.

1. Seleccione un **identificador** en la lista desplegable del cuadro **ID** o escriba un nuevo *identificador* en el cuadro **ID** .

1. Escriba la *clave* que desea usar como acelerador o haga clic con el botón derecho y elija **clave siguiente** con el tipo para establecer una combinación de teclas, o bien vaya a menú **Editar** > **siguiente clave con tipo**.

1. Cambie el **modificador** y **Escriba**, si es necesario, y presione **entrar**.

> [!NOTE]
> Asegúrese de que todos los aceleradores que defina sean únicos. Puede tener varias combinaciones de claves asignadas al mismo identificador sin ningún efecto incorrecto; por ejemplo, **Ctrl**+**P** y **F8** pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien, por ejemplo, **Ctrl**+**Z** asignada a ID_SPELL_CHECK y ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Para eliminar una entrada de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Seleccione la entrada que desea eliminar o mantenga presionada la tecla **Ctrl** o **MAYÚS** mientras selecciona la opción para elegir varias entradas.

1. Haga clic con el botón derecho y elija **eliminar**o vaya a menú **Editar** > **eliminar**.

> [!TIP]
> También puede presionar la tecla **suprimir** para eliminar.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Para mover o copiar una entrada de una tabla de aceleradores a otro archivo de script de recursos

1. Abra las tablas de aceleradores en los dos archivos de script de recursos y seleccione la entrada que desea trasladar.

1. En el menú **edición** , elija **copiar** o **cortar**.

1. Seleccione una entrada en el archivo de script de recursos de destino y, en el menú **edición** , elija **pegar**.

> [!NOTE]
> También puede usar las teclas de método abreviado para copiar y pegar.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para cambiar las propiedades de varias teclas de aceleración

1. Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Seleccione las teclas de aceleración que desea cambiar manteniendo presionada la tecla **Ctrl** mientras selecciona cada una.

1. Vaya al [ventana Propiedades](/visualstudio/ide/reference/properties-window) y escriba los valores que desea que compartan todos los aceleradores seleccionados.

> [!NOTE]
> Cada valor modificador aparece como una propiedad booleana en la ventana **propiedades** . Si cambia un valor de [modificador](../windows/accelerator-modifier-property.md) en la ventana **propiedades** , la tabla de aceleradores tratará el nuevo modificador como una adición a los modificadores que antes estaban allí. Por este motivo, si establece los valores de modificador, deberá establecer todos ellos para asegurarse de que cada acelerador comparte la misma configuración de **modificador** .

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Teclas de aceleración](../windows/predefined-accelerator-keys.md)<br/>
