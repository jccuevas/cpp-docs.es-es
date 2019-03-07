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
ms.openlocfilehash: f57c09d549a4ceb92db21c06499b4f6e71fc6a52
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/07/2019
ms.locfileid: "57562951"
---
# <a name="accelerator-editor-c"></a>Editor de aceleradores (C++)

Una tabla de aceleradores es un recurso de Windows de C++ que contiene una lista de teclas de aceleración, conocido como teclas de método abreviado y los identificadores de comandos que están asociados con ellas. Un programa puede tener más de una tabla de aceleradores.

Normalmente, los aceleradores se usan como métodos abreviados de teclado para comandos de programa que también están disponibles en un menú o una barra de herramientas. Sin embargo, puede usar la tabla de aceleradores para definir las combinaciones de teclas para los comandos que no tienen asociado un objeto de interfaz de usuario.

> [!TIP]
> Cuando se usa el **Editor de aceleradores**, con el botón secundario para mostrar un menú contextual de comandos frecuentes. Los comandos disponibles dependen del objeto al que apunta el puntero.

Puede usar la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para enlazar comandos de teclas de aceleración al código. Para obtener una lista de teclas de aceleración predefinidas, vea [teclas de aceleración](../windows/predefined-accelerator-keys.md).

> [!NOTE]
> Windows no permiten crear tablas de aceleradores vacías. Si crea una tabla de aceleradores sin entradas, se elimina automáticamente al guardar la tabla.

## <a name="accelerator-properties"></a>Propiedades de Acelerador

Puede establecer propiedades de acelerador el [ventana propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede usar el **Editor de aceleradores** para modificar las propiedades de Acelerador de la tabla de aceleradores. Los cambios realizados mediante el **propiedades** ventana o el **Editor de aceleradores** tienen el mismo resultado, las modificaciones se reflejan inmediatamente en la tabla de aceleradores.

El **ID** propiedad hace referencia a cada entrada de la tabla de aceleradores en código de programa. Esta entrada es el valor del comando que el programa recibe cuando un usuario presiona la tecla de aceleración o una combinación de teclas. Para realizar un acelerador igual que un elemento de menú, asegúrese del **Id. de** el mismo, siempre y cuando la **Id. de** del Acelerador de la tabla es el mismo que el **ID** para el recurso de menú.

Cada acelerador **ID** tiene tres propiedades: **Modificador**, **clave**, y **tipo**

El **modificador** propiedad establece el control de combinaciones de teclas para el acelerador.

> [!NOTE]
> En el **propiedades** ventana, el **modificador** propiedad aparece como tres independiente **booleano** propiedades, que puede controlarse de forma independiente: **ALT**, **Ctrl**, y **MAYÚS**.

Los siguientes son entradas legales para el **modificador** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |**Ninguno**|Usuario presiona sólo el **clave** valor.<br/><br/>Este valor se utiliza la forma más eficaz con los valores ASCII/ANSI 001 a 026, que se interpreta como ^ A ^ Z (**CTRL+a** a través de **CTRL+z**).|
   |**Alt**|El usuario debe presionar **Alt** antes de la **clave** valor.|
   |**Ctrl**|El usuario debe presionar **Ctrl** antes de la **clave** valor, no es válido con el tipo de ASCII.|
   |**Mayús**|El usuario debe presionar **MAYÚS** antes de la **clave** valor.|
   |**Ctrl+Alt**|El usuario debe presionar **Ctrl** y **Alt** antes de la **clave** valor, no es válido con el tipo de ASCII.|
   |**CTRL + MAYÚS**|El usuario debe presionar **Ctrl** y **MAYÚS** antes de la **clave** valor, no es válido con el tipo de ASCII.|
   |**ALT + MAYÚS**|El usuario debe presionar **Alt** y **MAYÚS** antes de la **clave** valor, no es válido con el tipo de ASCII.|
   |**Ctrl + Alt + Mayús**|El usuario debe presionar **Ctrl**, **Alt**, y **MAYÚS** antes de la **clave** valor, no es válido con el tipo de ASCII.|

El **clave** propiedad establece la clave real que se usará como el acelerador.

Los siguientes son entradas legales para el **clave** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |Un entero entre 0 y 255 en formato decimal.|El valor determina si el valor se trata como ASCII o ANSI como sigue:<br/><br/>   -Números de dígito siempre se interpretan como la clave correspondiente, en lugar de como valores ASCII o ANSI.<br/>   -Los valores de 1 a 26, si van precedidos de ceros, se interpretan como ^ A ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presiona con la **Ctrl** clave se mantiene presionada.<br/>   -Valores 27-32 siempre se interpretan como valores de tres dígitos decimales comprendidos entre 032 027.<br/>   -Los valores de 033 a 255, ya sea precedido de 0 o no se interpretan como valores ANSI.|
   |Un carácter único teclado.|Mayúscula A - Z o los números 0 - 9 pueden ser ASCII o valores de clave virtuales. Cualquier otro carácter solo es ASCII.|
   |Un carácter único teclado en el intervalo A - Z (sólo mayúsculas), precedida por un símbolo de intercalación (^), por ejemplo, ^ C.|Esta opción especifica el valor de ASCII de la clave cuando se presiona con la **Ctrl** tecla presionada.|
   |Cualquier identificador de clave virtual válido.|La lista desplegable **clave** cuadro en la tabla de aceleradores contiene una lista de identificadores de clave virtuales estándares.|

> [!NOTE]
> Al especificar un valor ASCII, el **modificador** se limitan las opciones de propiedad. La única clave de control disponible para su uso es la **Alt** clave.

> [!TIP]
> Un acceso directo para definir una tecla de aceleración es contextual una entrada o varias entradas en la tabla de aceleradores, a continuación, elija **tecla siguiente** y pulse cualquiera de las claves o combinaciones de teclas del teclado.
>
> Esto **tecla siguiente** comando también está disponible desde el **editar** menú.

El **tipo** propiedad determina si la combinación de teclas de método abreviado asociada con el Acelerador **ID** se interpreta como un valor de clave ASCII/ANSI o una combinación de tecla virtual (VIRTKEY).

- Si el **tipo** propiedad es **ASCII**, el **modificador** sólo puede ser propiedad `None` o `Alt`, o puede tener un acelerador que usa el **Ctrl** clave, como se especifica utilizando delante de la clave con un `^`.

- Si el **tipo** propiedad es **VIRTKEY**, cualquier combinación de **modificador** y **clave** valores es válido.

> [!NOTE]
> Si desea especificar un valor en la tabla de aceleradores y tienen el valor que se tratan como ASCII/ANSI, seleccione el **tipo** para la entrada en la tabla y seleccione **ASCII** en la lista desplegable. Sin embargo, si usa el **tecla siguiente** comando desde el **editar** menú para especificar el **clave**, debe cambiar la **tipo** propiedad desde **VIRTKEY** a **ASCII** *antes* escribir el **clave** código.

## <a name="accelerator-tables"></a>Tablas de aceleradores

En un proyecto de C++, puede editar una tabla de aceleradores directamente con la edición en contexto en el **Editor de aceleradores**.

Los procedimientos siguientes hacen referencia al uso de páginas de propiedades estándar, sin embargo, tanto la edición en contexto y el método de página de propiedad tienen el mismo resultado. Los cambios realizados mediante las páginas de propiedades o mediante la edición en contexto se reflejan inmediatamente en la tabla de aceleradores.

### <a name="to-edit-in-an-accelerator-table"></a>Para editar el contenido de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](/windows/how-to-create-a-resource-script-file#create-resources).

1. Seleccione una entrada en la tabla y seleccione esta opción para activar la edición en contexto.

1. Seleccione en el cuadro combinado desplegable o escriba en su lugar para realizar cambios:

   - Para **ID**, seleccione en la lista o escriba para editar.

   - Para **modificador**, seleccione en la lista.

   - Para **clave**, seleccione en la lista o escriba para editar.

   - Para **tipo**, seleccione **ASCII** o **VIRTKEY** en la lista.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Para buscar una entrada en una tabla de aceleradores abierta:

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](/windows/how-to-create-a-resource-script-file#create-resources).

1. Seleccione un encabezado de columna para ordenar el contenido de la columna alfabéticamente. Por ejemplo, seleccione **ID** para mostrar alfabéticamente todos los identificadores de la tabla de aceleradores.

   A continuación, puede examinar la lista y buscar la entrada.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](/windows/how-to-create-a-resource-script-file#create-resources).

1. Haga doble clic en la tabla de aceleradores y elija **nuevo acelerador**, o seleccione la entrada de fila vacía en la parte inferior de la tabla.

1. Seleccione un **Id. de** en la lista desplegable en el **Id. de** cuadro o escriba un nuevo *Id. de* en el **Id. de** cuadro.

1. Tipo de la *clave* que desea usar como acelerador, o bien haga clic en y elija **tecla siguiente** para establecer una combinación de teclas o vaya al menú **editar**  >  **Tecla siguiente escrito**.

1. Cambiar el **modificador** y **tipo**, si es necesario y presione **ENTRAR**.

> [!NOTE]
> Asegúrese de que todos los aceleradores que defina sean únicos. Puede tener varias combinaciones de teclas asignadas al mismo identificador no tiene ningún efecto negativos, por ejemplo, **Ctrl**+**P** y **F8** pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien, por ejemplo, **Ctrl**+**Z** asignado a tanto a ID_SPELL_CHECK como a ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Para eliminar una entrada de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](/windows/how-to-create-a-resource-script-file#create-resources).

1. Seleccione la entrada que desee eliminar, o mantenga presionada la **Ctrl** o **MAYÚS** clave durante la selección para elegir varias entradas.

1. Haga clic en y elija **eliminar**, o bien vaya al menú **editar** > **eliminar**.

> [!TIP]
> También puede presionar el **eliminar** clave va a eliminar.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Para mover o copiar una entrada de una tabla de aceleradores a otro archivo de script de recursos

1. Abra las tablas de aceleradores en los dos archivos de script de recursos y seleccione la entrada que desee mover.

1. Desde el **editar** menú, elija **copia** o **cortar**.

1. Seleccione una entrada en el archivo de script de recursos de destino y desde el **editar** menú, elija **pegar**.

> [!NOTE]
> También puede usar las teclas de método abreviado para copiar y pegar.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para cambiar las propiedades de varias teclas de aceleración

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](/windows/how-to-create-a-resource-script-file#create-resources).

1. Seleccione las teclas de aceleración que desee cambiar, mantenga presionada la **Ctrl** clave mientras selecciona cada uno de ellos.

1. Vaya a la [ventana propiedades](/visualstudio/ide/reference/properties-window) y escriba los valores que desea que todos los aceleradores seleccionados para compartir.

> [!NOTE]
> Cada valor de modificador aparece como una propiedad booleana en el **propiedades** ventana. Si cambia un [modificador](../windows/accelerator-modifier-property.md) valor en el **propiedades** ventana, la tabla de aceleradores tratará al nuevo modificador como una adición a los modificadores que previamente contenía. Por este motivo, si establece los valores de modificador, se deberá establecer todos ellos para asegurarse de que todos los aceleradores compartan la misma **modificador** configuración.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Teclas de aceleración](../windows/predefined-accelerator-keys.md)<br/>