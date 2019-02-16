---
title: Creación de menús (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: da5fc355ae11ee5efb1c58be9e33bd4fb8bff02d
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320528"
---
# <a name="creating-menus-c"></a>Creación de menús (C++)

> [!NOTE]
> El **ventana recursos** no está disponible en las ediciones Express.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-a-standard-menu"></a>Crear un menú estándar

1. Desde el **vista** menú, seleccione **vista de recursos** y, a continuación, haga doble clic en el **menú** de encabezado y elija **Agregar recurso**. Elija **Menú**.

1. Seleccione el cuadro **Nuevo elemento** (el rectángulo que contiene "Escriba aquí") en la barra de menús.

   ![Cuadro nuevo elemento en el editor de menús](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Cuadro Nuevo elemento

1. Escriba un nombre para el nuevo menú, por ejemplo, "Archivo".

   El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   Tras asignar un nombre al nuevo menú en la barra de menús, el cuadro de nuevo elemento se desplaza hacia la derecha (para permitir agregar otro menú) y se abre otro cuadro de nuevo elemento debajo del primer menú, donde pueden agregarse otros comandos de menú.

   ![Cuadro nuevo elemento expandido](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Cuadro Nuevo elemento con el foco desplazado al escribir el nombre del nuevo menú

   > [!NOTE]
   > Para crear un solo elemento de menú en la barra de menús, establezca la **emergente** propiedad **False**.

## <a name="create-a-submenu"></a>Crear un submenú

1. Seleccione el comando de menú para el que desea crear un submenú.

1. En el cuadro **Nuevo elemento** que aparece a la derecha, escriba el nombre del nuevo comando de menú. Este nuevo comando aparecerá primero en el menú del submenú.

1. Agregar otros comandos de menú al menú del submenú.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Para insertar un nuevo menú entre los menús existentes

Seleccione un nombre en el menú de existentes y presione la **insertar** clave. El **nuevo elemento** cuadro se inserta antes del elemento seleccionado.

   \- o -

Haga doble clic en la barra de menús y elija **Insertar nuevo** en el menú contextual.

## <a name="add-commands-to-a-menu"></a>Agregar comandos a un menú

1. Crear un menú.

1. Seleccione un nombre de menú, por ejemplo, **archivo**.

   Cada menú se expandirá y expondrá un nuevo cuadro de elemento para los comandos. Por ejemplo, puede agregar los comandos **New**, **abierto**, y **cerrar** a un **archivo** menú.

1. En el nuevo cuadro de elemento, escriba un nombre para el nuevo comando de menú.

   > [!NOTE]
   > El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   > [!TIP]
   > Puede definir una tecla nemotécnica (tecla de acceso rápido) que permita al usuario seleccionar el comando de menú. Escriba una y comercial (`&`) delante de una letra para especificarla como la tecla de acceso. El usuario puede seleccionar el comando de menú escribiendo esa letra.

1. En el **propiedades** ventana, seleccione el menú de comandos propiedades que se aplican. Para obtener más información, consulte [propiedades de comando de menú](../windows/menu-command-properties.md).

1. En el **símbolo del sistema** cuadro el **propiedades** ventana, escriba la cadena del mensaje que desea que aparezcan en la barra de estado de la aplicación.

   Este paso crea una entrada en la tabla de cadenas con el mismo identificador de recursos que el comando de menú que creó.

   > [!NOTE]
   > Avisos solo afectan a los elementos de menú con un **emergente** propiedad de **True**. Por ejemplo, los elementos de menú de nivel superior pueden tener avisos si tienen elementos de submenú. El propósito de un **Prompt** es indicar lo que ocurrirá si un usuario selecciona el elemento de menú.

1. Presione **ENTRAR** para completar el comando de menú.

   El cuadro de elemento nuevo se selecciona para que pueda crear comandos de menú adicionales.

## <a name="create-pop-up-menus"></a>Crear menús emergentes

Los[menús emergentes](../mfc/menus-mfc.md) muestran comandos de pantalla que se utilizan con frecuencia. Pueden ser contextuales con respecto a la ubicación del puntero. Utilizar menús emergentes en la aplicación requiere compilar el menú y, a continuación, conectarlo al código de la aplicación.

Una vez haya creado el recurso de menú, el código de aplicación debe cargar el recurso y usar [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) para que aparezca el menú. Una vez que el usuario descarte el menú emergente seleccionando fuera de él, o ha seleccionado un comando, se devolverá esa función. Si el usuario elige un comando, se enviará el mensaje de ese comando a la ventana cuyo controlador se ha pasado.

### <a name="to-create-a-pop-up-menu"></a>Para crear un menú emergente

1. [Cree un menú](../windows/creating-a-menu.md) con un título vacío (no proporcione ningún **Título**).

1. [Agregue un comando de menú al menú nuevo](../windows/adding-commands-to-a-menu.md). Mover al primer comando de menú debajo del título de menú en blanco (el título provisional dice `Type Here`). Escriba un **Título** y cualquier otra información.

   Repita este proceso para los demás comandos de menú del menú emergente.

1. Guarde el recurso de menú.

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Para conectar un menú emergente a una aplicación

1. Agregue un controlador de mensajes para WM_CONTEXTMENU (por ejemplo). Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

1. Agregue el código siguiente al controlador de mensajes:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > El [CPoint](../atl-mfc-shared/reference/cpoint-class.md) pasa por el mensaje de controlador está en coordenadas de pantalla.

   > [!NOTE]
   > Conectar un menú emergente a una aplicación requiere MFC.

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Para ver un recurso de menú como menú emergente

Normalmente, cuando esté trabajando el **menú** editor, un recurso de menú se muestra como una barra de menús. Sin embargo, es posible que algunos recursos de menú se agreguen a la barra de menús de la aplicación mientras se ejecuta el programa.

El menú contextual y elija **ver como emergente** en el menú contextual.

   Esta opción es sólo una preferencia de visualización y no modificará su menú.

   > [!NOTE]
   > Para cambiar a la vista de la barra de menús, haga clic en **ver como emergente** nuevo (que quita la marca de verificación y devuelve la vista de la barra de menús).

## <a name="edit-multiple-menus-or-menu-commands"></a>Editar varios menús o comandos de menú

### <a name="to-select-multiple-menu-commands"></a>Para seleccionar varios comandos de menú

Puede seleccionar varios nombres de los menús o comandos de menú para ejecutar operaciones masivas, como eliminar o cambiar las propiedades.

Mientras mantiene presionada la **Ctrl** clave, seleccione los menús o comandos de submenú que desee.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Para mover y copiar menús y comandos de menú

Puede mover o copiar menús y comandos de menú mediante el método de arrastrar y colocar o usando los comandos del menú contextual (menú que se abre al hacer clic con el botón derecho).

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Para mover o copiar menús o comandos de menú mediante el método de arrastrar y colocar

1. Arrastre o copie el elemento que desee mover a:

   - Una nueva ubicación en el menú actual.

   - Otro menú. (Puede navegar a otros menús arrastrando el puntero del mouse sobre ellos).

1. Arrastre el comando de menú cuando la guía de inserción muestre la posición que desee.

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Para mover o copiar menús o comandos de menú mediante los comandos de menú contextual

1. Haga clic con el botón derecho en uno o varios menús o comandos de menú.

1. En el menú contextual, elija **Cortar** (para mover) o **Copiar**.

1. Si va a mover los elementos al menú de otro recurso o archivo de script de recursos, [abrirlo en otra ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Seleccione la posición del menú o comando de menú al que desee mover o copiar.

1. En el menú contextual, elija **Pegar**. El elemento movido o copiado se coloca antes del elemento que seleccione.

   > [!NOTE]
   > También puede arrastrar, copiar y pegar en otros menús de otras ventanas de menú.

### <a name="to-delete-a-menu-or-menu-command"></a>Para eliminar un menú o un comando de menú

1. Haga clic con el botón derecho en un nombre de menú o de comando.

1. Seleccione **Eliminar** en el menú contextual.

   > [!NOTE]
   > De forma similar, puede utilizar el menú contextual para realizar otras acciones, como Copiar, Cortar, Pegar, Insertar nuevo, Insertar separador, Editar IDs, Ver como emergente, Comprobar teclas de acceso, etc.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)