---
title: Comandos de menú (C++)
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
ms.openlocfilehash: c9abf46907c473d4cf6d9e945038f70aa75bfc48
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026284"
---
# <a name="menu-commands-c"></a>Comandos de menú (C++)

La siguiente información se organiza según el **menú** propiedades que aparecen en la [ventana propiedades](/visualstudio/ide/reference/properties-window) cuando se selecciona un comando de menú. Están ordenadas alfabéticamente, aunque el **propiedades** ventana también le permite ver estas propiedades por categoría.

|Propiedad|Descripción|
|--------------|-----------------|
|**Break**|Puede ser uno de estos valores:<br/>  - **Ninguno**: Sin interrupción. Este es el valor predeterminado.<br/>  - **Columna**: En los menús estáticos, este valor sitúa el comando de menú en una nueva línea.<br/>      En los menús emergentes, este valor sitúa el comando de menú en una columna nueva, sin línea divisoria entre las columnas.<br/>      Esta propiedad solo afecta a la apariencia del menú en tiempo de ejecución, no en el editor de menús.<br />   - **Bar**: Igual que **columna** , excepto en los menús emergentes, este valor separa la nueva columna de la columna antigua con una línea vertical.<br/>      Esta propiedad afecta a la apariencia del menú en tiempo de ejecución, no en el **Editor de menús**.|
|**Título**|El texto que etiqueta el comando de menú (el nombre del menú). Para convertir una de las letras del título de un comando de menú en la tecla de acceso, sitúe delante de ella una Y comercial (&).|
|**Activadas**|Si **True**, el comando de menú se activa inicialmente. Tipo: **BOOL**. Predeterminado: **False**.|
|**Habilitado**|Si es **False**, se deshabilita el elemento de menú.|
|**Grayed**|Si **True**, el comando de menú inicialmente está atenuado e inactivo. Tipo: **BOOL**. Predeterminado: **False**.|
|**Ayuda**|Alinea el elemento de menú a la derecha. Predeterminado: **False**.<br/><br/>Por ejemplo, el comando de menú **Ayuda** siempre está a la derecha en todas las aplicaciones de Windows. Si establece esta propiedad en un elemento de menú, ese elemento aparecerá en el extremo derecho y al final del menú. Se aplica a los elementos de nivel superior.|
|**ID**|Un símbolo definido en el archivo de encabezado. Tipo: **Símbolo**, **entero**, o **cadena entrecomillada**.<br/><br/>Puede usar cualquier símbolo de los que se encuentran disponibles normalmente en cualquier editor, aunque la [ventana Propiedades](/visualstudio/ide/reference/properties-window) no proporciona ninguna lista desplegable donde seleccionar.|
|**Popup**|Si **True**, el comando de menú es un menú emergente. Tipo: **BOOL**. Predeterminado: **True** para los menús de nivel superior de una barra de menús, en caso contrario **False**.|
|**Preguntar**|Contiene el texto que aparece en la barra de estado cuando se resalta el comando de menú. El texto se sitúa en la tabla de cadenas con el mismo identificador que el comando de menú.<br/><br/>Esta propiedad se encuentra disponible para cualquier tipo de proyecto, pero la funcionalidad en tiempo de ejecución es específica de MFC.|
|**Right to Left Justify**|Justifica a la derecha el comando de menú en la barra de menús, en tiempo de ejecución. Tipo: **BOOL**. Predeterminado: **False**.|
|**Right to Left Order**|Permite mostrar los comandos de menú de derecha a izquierda cuando la interfaz se localiza a idiomas con esta dirección de lectura, como el hebreo o el árabe.|
|**Separator**|Si **True**, el comando de menú es un separador. Tipo: **BOOL**. Predeterminado: **False**.|

## <a name="associate-menu-commands"></a>Asociar comandos de menú

A menudo quiere que un elemento de menú u una combinación de teclado ejecuten el mismo comando de programa. Se emiten comandos idéntico utilizando el **Editor de menús** para asignar el mismo identificador de recurso para el comando de menú y a una entrada en la tabla de aceleradores de la aplicación. A continuación, edite el [Título](../windows/menu-command-properties.md) del comando de menú para que muestre el nombre del acelerador.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Para asociar un comando de menú a una tecla de aceleración

1. En el **Editor de menús**, seleccione el comando de menú que desee.

1. En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue el nombre de la tecla de aceleración a la propiedad **Título** :

   - Tras el título del menú, escriba la secuencia de escape de una tabulación (\t), para que todas las teclas de aceleración del menú quedan alineadas.

   - Escriba el nombre de la tecla modificadora (**Ctrl**, **Alt**, o **MAYÚS**) seguido por un signo más (**+**) y el nombre, la carta, o símbolo de la tecla adicional.

   Por ejemplo, para asignar **Ctrl**+**O** a la **abierto** comando el **archivo** menú, modifique el comando de menú  **Título** para que quede como el siguiente texto:

   ```
   &Open...\tCtrl+O
   ```

   El comando de menú en el **Editor de menús** se actualiza para reflejar el nuevo título a medida que lo escribe.

1. [Cree la entrada de la tabla de aceleradores](../windows/adding-an-entry-to-an-accelerator-table.md) en el editor **Acelerador** y asígnele el mismo identificador que el comando de menú. Use una combinación de teclas que le resulte sencilla de recordar.

La aplicación de MFC puede mostrar texto descriptivo para cada uno de los comandos de menú, que puede seleccionar un usuario. Mostrar texto descriptivo, se asigna una cadena de texto a cada comando de menú mediante el **Prompt** propiedad en el **propiedades** ventana. Si tiene una cadena en la [tabla de cadenas](../windows/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.

- Para asociar un comando de menú con la cadena de texto en aplicaciones MFC, la barra de estado en el **Editor de menús**, seleccione el comando de menú. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba el texto de la barra de estado asociado en el cuadro **Prompt** .

En un proyecto de C++, puede asignar una tecla de acceso (una tecla de acceso que permite al usuario seleccionar el menú con el teclado) para los menús y comandos de menú.

- Para asignar una tecla de acceso (método abreviado) a un comando de menú, escriba una y comercial (`&`) delante de una letra en el nombre de menú o el nombre de comando para especificar esa letra como tecla de acceso correspondiente. 

   Por ejemplo, "& archivo" define **Alt**+**F** como tecla de método abreviado para el **archivo** menú en aplicaciones escritas para Microsoft Windows.

   El elemento de menú ofrecerá una indicación visible de que una de las letras tiene asignada una tecla de método abreviado. La letra que sigue a la y comercial aparece subrayada (depende del sistema operativo).

> [!NOTE]
> Asegúrese de que todas las claves de acceso en un menú son únicas, haciendo clic en el menú y elegir **Comprobar teclas de acceso**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)<br/>

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->