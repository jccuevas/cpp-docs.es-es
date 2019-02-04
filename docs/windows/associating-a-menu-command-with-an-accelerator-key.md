---
title: Asociar comandos de menú (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703043"
---
# <a name="associating-menu-commands-c"></a>Asociar comandos de menú (C++)

A menudo quiere que un elemento de menú u una combinación de teclado ejecuten el mismo comando de programa. Se emiten comandos idéntico utilizando el **menú** editor para asignar el mismo identificador de recurso para el comando de menú y a una entrada en la tabla de aceleradores de la aplicación. A continuación, edite el [Título](../windows/menu-command-properties.md) del comando de menú para que muestre el nombre del acelerador.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Para asociar un comando de menú a una tecla de aceleración

1. En el editor de **menús** , seleccione el comando de menú que quiere.

1. En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), agregue el nombre de la tecla de aceleración a la propiedad **Título** :

   - Tras el título del menú, escriba la secuencia de escape de una tabulación (\t), para que todas las teclas de aceleración del menú quedan alineadas.

   - Escriba el nombre de la tecla modificadora (**Ctrl**, **Alt**, o **MAYÚS**) seguido por un signo más (**+**) y el nombre, la carta, o símbolo de la tecla adicional.

       Por ejemplo, para asignar **Ctrl**+**O** a la **abierto** comando el **archivo** menú, modifique el comando de menú  **Título** para que quede como el siguiente texto:

        ```
        &Open...\tCtrl+O
        ```

       El comando de menú en el **menú** editor se actualiza para reflejar el nuevo título a medida que lo escribe.

1. [Cree la entrada de la tabla de aceleradores](../windows/adding-an-entry-to-an-accelerator-table.md) en el editor **Acelerador** y asígnele el mismo identificador que el comando de menú. Use una combinación de teclas que le resulte sencilla de recordar.

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>Para asociar un comando de menú a un cadena de texto en aplicaciones MFC de la barra de estado

La aplicación de MFC puede mostrar texto descriptivo para cada uno de los comandos de menú, que puede seleccionar un usuario. Mostrar texto descriptivo, se asigna una cadena de texto a cada comando de menú mediante el **Prompt** propiedad en el **propiedades** ventana. Si tiene una cadena en la [tabla de cadenas](../windows/string-editor.md) cuyo id. es igual que el comando, una aplicación MFC mostrará automáticamente este recurso de cadena en la barra de estado de la aplicación en ejecución cuando un usuario se desplace sobre un elemento de menú.

1. En el editor de **menús** , seleccione el comando de menú.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), escriba el texto de la barra de estado asociado en el cuadro **Prompt** .

> [!NOTE]
> Este conjunto de pasos requiere MFC.

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Para asignar una tecla de acceso (método abreviado) a un comando de menú

En un proyecto de C++, puede asignar una tecla de acceso (una tecla de acceso que permite al usuario seleccionar el menú con el teclado) para los menús y comandos de menú.

Escriba una y comercial (`&`) delante de una letra en el nombre de menú o el nombre de comando para especificar esa letra como tecla de acceso correspondiente. Por ejemplo, "& archivo" define **Alt**+**F** como tecla de método abreviado para el **archivo** menú en aplicaciones escritas para Microsoft Windows.

   El elemento de menú ofrecerá una indicación visible de que una de las letras tiene asignada una tecla de método abreviado. La letra que sigue a la y comercial aparece subrayada (depende del sistema operativo).

   > [!NOTE]
   > Para asegurarse de que todas las teclas de acceso de un menú son únicas, haga clic con el botón secundario en el menú y elija **Comprobar teclas de acceso** en el menú contextual.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)<br/>
[Adición de comandos a un menú](../windows/adding-commands-to-a-menu.md)<br/>
[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
