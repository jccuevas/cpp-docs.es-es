---
title: Editor de menús (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: b5d809fa4e0f608d4c0e6cbdaf8697688c6d3f9c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376791"
---
# <a name="menu-editor-c"></a>Editor de menús (C++)

Los menús le permiten organizar comandos de una forma lógica y sencilla de encontrar. Con el **Editor de menús**, puede crear y editar menús trabajando directamente con una barra de menús es muy similar a uno en la aplicación finalizada.

> [!TIP]
> Al usar el **Editor de menús**, en muchos casos, puede hacer clic en para mostrar un menú emergente de comandos usados con frecuencia. Los comandos disponibles dependen del objeto al que apunta el puntero.

## <a name="how-to"></a>Procedimientos

El **Editor de menús** le permite:

### <a name="to-create-a-standard-menu"></a>Para crear un menú estándar

1. Vaya al menú **vista** > **vista de recursos** y haga doble clic en el **menú** encabezado. Elija **Agregar recurso**, a continuación, **menú**.

1. Seleccione el **nuevo elemento** cuadro (el rectángulo que contiene *escriba aquí*) en la barra de menús.

   ![Cuadro nuevo elemento en el editor de menús](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **Nuevo elemento** cuadro

1. Escriba un nombre para el nuevo menú, por ejemplo, *archivo*.

   El texto que escriba aparecerá en el **Editor de menús** y en el **título** cuadro el [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   Tras asignar un nombre al nuevo menú en la barra de menús, el cuadro de nuevo elemento se desplaza hacia la derecha (para permitir agregar otro menú) y se abre otro cuadro de nuevo elemento debajo del primer menú, donde pueden agregarse otros comandos de menú.

   ![Cuadro nuevo elemento expandido](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **Nuevo elemento** cuadro con el foco desplazado al escribir el nombre del menú

   > [!NOTE]
   > Para crear un solo elemento de menú en la barra de menús, establezca la **emergente** propiedad **False**.

### <a name="to-create-a-submenu"></a>Para crear un submenú

1. Seleccione el comando de menú para el que desea crear un submenú.

1. En el cuadro **Nuevo elemento** que aparece a la derecha, escriba el nombre del nuevo comando de menú. Este nuevo comando aparecerá primero en el menú del submenú.

1. Agregar otros comandos de menú al menú del submenú.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Para insertar un nuevo menú entre los menús existentes

Seleccione un nombre en el menú de existentes y presione la **insertar** clave, o haga doble clic en la barra de menús y elija **Insertar nuevo**.

   El **nuevo elemento** cuadro se inserta antes del elemento seleccionado.

### <a name="to-add-commands-to-a-menu"></a>Para agregar comandos a un menú

1. Crear un menú. A continuación, seleccione un nombre de menú, por ejemplo, **archivo**.

   Cada menú se expandirá y expondrá un nuevo cuadro de elemento para los comandos. Por ejemplo, puede agregar los comandos **New**, **abierto**, y **cerrar** a un **archivo** menú.

1. En el nuevo cuadro de elemento, escriba un nombre para el nuevo comando de menú.

   > [!NOTE]
   > El texto que escriba aparecerá en el **Editor de menús** y en el **título** cuadro el [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   > [!TIP]
   > Puede definir una tecla nemotécnica (tecla de acceso rápido) que permita al usuario seleccionar el comando de menú. Escriba una y comercial (`&`) delante de una letra para especificarla como la tecla de acceso. El usuario puede seleccionar el comando de menú escribiendo esa letra.

1. En el **propiedades** ventana, seleccione el menú de comandos propiedades que se aplican. Para obtener más información, consulte [propiedades de comando de menú](../windows/menu-command-properties.md).

1. En el **símbolo del sistema** cuadro el **propiedades** ventana, escriba la cadena del mensaje que desea que aparezcan en la barra de estado de la aplicación.

   Este paso crea una entrada en la tabla de cadenas con el mismo identificador de recursos que el comando de menú que creó.

   > [!NOTE]
   > Avisos solo afectan a los elementos de menú con un **emergente** propiedad de **True**. Por ejemplo, los elementos de menú de nivel superior pueden tener avisos si tienen elementos de submenú. El propósito de un **Prompt** es indicar lo que ocurrirá si un usuario selecciona el elemento de menú.

1. Presione **ENTRAR** para completar el comando de menú.

   El cuadro de elemento nuevo se selecciona para que pueda crear comandos de menú adicionales.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Para seleccionar varios comandos de menú para ejecutar operaciones masivas, como eliminar o cambiar propiedades

Mientras mantiene presionada la **Ctrl** clave, seleccione los menús o comandos de submenú que desee.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Para mover y copiar menús y comandos de menú

- Utilice el método de arrastrar y colocar:

   1. Arrastre o copie el elemento que desee mover a:

      - Una nueva ubicación en el menú actual.

      - Otro menú. Puede navegar a otros menús arrastrando el puntero del mouse sobre ellos.

   1. Arrastre el comando de menú cuando la guía de inserción muestre la posición que desee.

- Use los comandos del menú contextual:

   1. Haga clic en uno o varios menús o comandos de menú y luego elija **cortar** (para mover) o **copia**.

   1. Si va a mover los elementos al menú de otro recurso o archivo de script de recursos, [abrirlo en otra ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Seleccione la posición del menú o comando de menú al que desee mover o copiar.

   1. En el menú contextual, elija **Pegar**. El elemento movido o copiado se coloca antes del elemento que seleccione.

> [!NOTE]
> También puede arrastrar, copiar y pegar en otros menús de otras ventanas de menú.

### <a name="to-delete-a-menu-or-menu-command"></a>Para eliminar un menú o un comando de menú

Haga clic en el nombre del menú o comando y elija **eliminar**.

> [!NOTE]
> De forma similar, puede utilizar el menú contextual para realizar otras acciones, como Copiar, Cortar, Pegar, Insertar nuevo, Insertar separador, Editar IDs, Ver como emergente, Comprobar teclas de acceso, etc.

## <a name="pop-up-menus"></a>Menús emergentes

Los[menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.

Una vez haya creado el recurso de menú, el código de aplicación debe cargar el recurso y usar [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) para que aparezca el menú. Una vez que el usuario descarte el menú emergente seleccionando fuera de él, o ha seleccionado un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.

> [!NOTE]
> Para los programas de la biblioteca de Microsoft Foundation Class (MFC) y los programas ATL, use **asistentes para código** para enlazar comandos de menú al código. Para obtener más información, consulte [agregar un evento](../ide/adding-an-event-visual-cpp.md) y [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

- Para crear un menú emergente, crear un menú con un título vacío y no proporcionan un *título*. A continuación, agregue un comando de menú al menú nuevo, pasar al primer comando de menú debajo del título de menú en blanco con el título provisional *escriba aquí* y escriba un *título* y cualquier otra información.

   Repita este proceso para cualquier otro comando de menú en el menú emergente y asegúrese de guardar el recurso de menú.

- Para conectar un menú emergente a una aplicación, por ejemplo, agregue un controlador de mensajes para WM_CONTEXTMENU, a continuación, agregue el código siguiente al controlador de mensajes:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > El [CPoint](../atl-mfc-shared/reference/cpoint-class.md) pasa por el mensaje de controlador está en coordenadas de pantalla.

Normalmente, cuando esté trabajando el **Editor de menús**, un recurso de menú se muestra como una barra de menús. Sin embargo, es posible que algunos recursos de menú se agreguen a la barra de menús de la aplicación mientras se ejecuta el programa.

- Para ver un recurso de menú como menú emergente, haga clic en el menú y elija **ver como emergente**.

   Esta opción es sólo una preferencia de visualización y no modificará su menú.

> [!TIP]
> Para cambiar a la vista de la barra de menús, seleccione **ver como emergente** nuevo. Esta acción quita la marca de verificación y devuelve la vista de la barra de menús.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Comandos de menú](../windows/menu-command-properties.md)<br/>

<!--
[User-Interface Objects and Command IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](https://msdn.microsoft.com/library/windows/desktop/ms646977.aspx)-->