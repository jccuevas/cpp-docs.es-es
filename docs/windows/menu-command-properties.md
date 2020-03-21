---
title: Comandos de menúC++()
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: 972478923a7c4c60d8ff949c5532b00a1de1efc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075502"
---
# <a name="menu-commands-c"></a>Comandos de menúC++()

La información siguiente se organiza según las propiedades de **menú** que aparecen en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) al seleccionar un comando de menú. Se muestran en orden alfabético, aunque la ventana **propiedades** también le permite ver estas propiedades por categoría.

|Propiedad|Descripción|
|--------------|-----------------|
|**Break**|Puede ser uno de estos valores:<br/>  - **None**: sin interrupción. Este es el valor predeterminado.<br/>  - **Column**: en los menús estáticos, este valor sitúa el comando de menú en una nueva línea.<br/>      En los menús emergentes, este valor sitúa el comando de menú en una columna nueva, sin línea divisoria entre las columnas.<br/>      Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.<br />   **barra**de - : igual que la **columna** excepto, en el caso de los menús emergentes, este valor separa la nueva columna de la antigua con una línea vertical.<br/>      El establecimiento de esta propiedad afecta a la apariencia del menú solo en tiempo de ejecución, no en el **Editor de menús**.|
|**Caption**|El texto que etiqueta el comando de menú (el nombre del menú). Para convertir una de las letras del título de un comando de menú en la tecla de acceso, sitúe delante de ella una Y comercial (&).|
|**Activadas**|Si es **true**, el comando de menú se activa inicialmente. Tipo: **bool**. Valor predeterminado: **False**.|
|**Enabled**|Si es **False**, se deshabilita el elemento de menú.|
|**Grayed**|Si es **true**, el comando de menú se atenúa inicialmente y está inactivo. Tipo: **bool**. Valor predeterminado: **False**.|
|**Ayuda**|Alinea el elemento de menú a la derecha. Valor predeterminado: **False**.<br/><br/>Por ejemplo, el comando de menú **Ayuda** siempre está a la derecha en todas las aplicaciones de Windows. Si establece esta propiedad en un elemento de menú, ese elemento aparecerá en el extremo derecho y al final del menú. Se aplica a los elementos de nivel superior.|
|**Id**|Un símbolo definido en el archivo de encabezado. Tipo: **símbolo**, **entero**o **cadena entrecomillada**.<br/><br/>Puede usar cualquier símbolo de los que se encuentran disponibles normalmente en cualquier editor, aunque la [ventana Propiedades](/visualstudio/ide/reference/properties-window) no proporciona ninguna lista desplegable donde seleccionar.|
|**Popup**|Si es **true**, el comando de menú es un menú emergente. Tipo: **bool**. Valor predeterminado: **true** para los menús de nivel superior en una barra de menús; de lo contrario, **false**.|
|**Pregunta**|Contiene el texto que aparece en la barra de estado cuando se resalta el comando de menú. El texto se sitúa en la tabla de cadenas con el mismo identificador que el comando de menú.<br/><br/>Esta propiedad se encuentra disponible para cualquier tipo de proyecto, pero la funcionalidad en tiempo de ejecución es específica de MFC.|
|**Right to Left Justify**|Justifica a la derecha el comando de menú en la barra de menús, en tiempo de ejecución. Tipo: **bool**. Valor predeterminado: **False**.|
|**Right to Left Order**|Permite mostrar los comandos de menú de derecha a izquierda cuando la interfaz se localiza a idiomas con esta dirección de lectura, como el hebreo o el árabe.|
|**Separator**|Si es **true**, el comando de menú es un separador. Tipo: **bool**. Valor predeterminado: **False**.|

## <a name="associate-menu-commands"></a>Asociar comandos de menú

A menudo quiere que un elemento de menú u una combinación de teclado ejecuten el mismo comando de programa. Los comandos idénticos se emiten mediante el **Editor de menús** para asignar el mismo identificador de recurso al comando de menú y a una entrada de la tabla de aceleradores de la aplicación. A continuación, edite el [Título](../windows/menu-command-properties.md) del comando de menú para que muestre el nombre del acelerador.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Para asociar un comando de menú a una tecla de aceleración

1. En el **Editor de menús**, seleccione el comando de menú que desee.

1. En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue el nombre de la tecla de aceleración a la propiedad **Título** :

   - Tras el título del menú, escriba la secuencia de escape de una tabulación (\t), para que todas las teclas de aceleración del menú quedan alineadas.

   - Escriba el nombre de la tecla modificadora (**Ctrl**, **Alt**o **MAYÚS**) seguido de un signo más ( **+** ) y el nombre, la letra o el símbolo de la tecla adicional.

   Por ejemplo, para asignar **Ctrl**+**O** al comando **abrir** del menú **archivo** , modifique el **título** del comando de menú para que tenga el aspecto siguiente:

   ```
   &Open...\tCtrl+O
   ```

   El comando de menú del **Editor de menús** se actualiza para reflejar el nuevo título a medida que lo escribe.

1. [Cree la entrada de la tabla de aceleradores](../windows/adding-an-entry-to-an-accelerator-table.md) en el editor **Acelerador** y asígnele el mismo identificador que el comando de menú. Use una combinación de teclas que le resulte sencilla de recordar.

La aplicación MFC puede mostrar texto descriptivo para cada uno de los comandos de menú que puede seleccionar un usuario. Para mostrar texto descriptivo, asigne una cadena de texto a cada comando de menú mediante la propiedad **prompt** de la ventana **propiedades** . Si tiene una cadena en la [tabla de cadenas](../windows/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.

- Para asociar un comando de menú a una cadena de texto de la barra de estado en aplicaciones MFC, en el **Editor de menús**, seleccione el comando de menú. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba el texto de la barra de estado asociado en el cuadro **Prompt** .

En un C++ proyecto, puede asignar una tecla de acceso (un mnemotécnico que permita al usuario seleccionar el menú con el teclado) para los menús y comandos de menú.

- Para asignar una tecla de acceso (método abreviado) a un comando de menú, escriba una y comercial (`&`) delante de una letra en el nombre del menú o el nombre de comando para especificar esa letra como la tecla de acceso correspondiente.

   Por ejemplo, "archivo de &" establece **Alt**+**F** como la tecla de método abreviado para el menú **archivo** en las aplicaciones escritas para Microsoft Windows.

   El elemento de menú ofrecerá una indicación visible de que una de las letras tiene asignada una tecla de método abreviado. La letra que sigue a la y comercial aparece subrayada (depende del sistema operativo).

> [!NOTE]
> Asegúrese de que todas las teclas de acceso de un menú son únicas; para ello, haga clic con el botón derecho en el menú y elija **Comprobar teclas**de acceso.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editor de menús](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->