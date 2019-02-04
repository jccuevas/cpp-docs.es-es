---
title: Editar varios menús o comandos de menú (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703225"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>Editar varios menús o comandos de menú

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-menu-commands"></a>Para seleccionar varios comandos de menú

Puede seleccionar varios nombres de los menús o comandos de menú para ejecutar operaciones masivas, como eliminar o cambiar las propiedades.

Mientras mantiene presionada la **Ctrl** clave, seleccione los menús o comandos de submenú que desee.

## <a name="to-move-and-copy-menus-and-menu-commands"></a>Para mover y copiar menús y comandos de menú

Puede mover o copiar menús y comandos de menú mediante el método de arrastrar y colocar o usando los comandos del menú contextual (menú que se abre al hacer clic con el botón derecho).

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Para mover o copiar menús o comandos de menú mediante el método de arrastrar y colocar

1. Arrastre o copie el elemento que desee mover a:

   - Una nueva ubicación en el menú actual.

   - Otro menú. (Puede navegar a otros menús arrastrando el puntero del mouse sobre ellos).

1. Arrastre el comando de menú cuando la guía de inserción muestre la posición que desee.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Para mover o copiar menús o comandos de menú mediante los comandos de menú contextual

1. Haga clic con el botón derecho en uno o varios menús o comandos de menú.

1. En el menú contextual, elija **Cortar** (para mover) o **Copiar**.

1. Si va a mover los elementos al menú de otro recurso o archivo de script de recursos, [abrirlo en otra ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Seleccione la posición del menú o comando de menú al que desee mover o copiar.

1. En el menú contextual, elija **Pegar**. El elemento movido o copiado se coloca antes del elemento que seleccione.

   > [!NOTE]
   > También puede arrastrar, copiar y pegar en otros menús de otras ventanas de menú.

## <a name="to-delete-a-menu-or-menu-command"></a>Para eliminar un menú o un comando de menú

1. Haga clic con el botón derecho en un nombre de menú o de comando.

1. Seleccione **Eliminar** en el menú contextual.

   > [!NOTE]
   > De forma similar, puede utilizar el menú contextual para realizar otras acciones, como Copiar, Cortar, Pegar, Insertar nuevo, Insertar separador, Editar IDs, Ver como emergente, Comprobar teclas de acceso, etc.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)