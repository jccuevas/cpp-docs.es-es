---
title: Creación de un menú (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: b779e6b089410b818247471086fe987c37b1f36c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518565"
---
# <a name="creating-a-menu-c"></a>Creación de un menú (C++)

> [!NOTE]
> El **ventana recursos** no está disponible en las ediciones Express.

### <a name="to-create-a-standard-menu"></a>Para crear un menú estándar

1. En el menú **Ver** , haga clic en **Vista de recursos** y, a continuación, haga clic con el botón secundario en el encabezado **Menú** y elija **Agregar recurso**. Elija **Menú**.

2. Seleccione el cuadro **Nuevo elemento** (el rectángulo que contiene "Escriba aquí") en la barra de menús.

   ![Cuadro nuevo elemento en el editor de menús](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Cuadro Nuevo elemento

3. Escriba un nombre para el nuevo menú, por ejemplo, "Archivo".

   El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.

   Tras asignar un nombre al nuevo menú en la barra de menús, el cuadro de nuevo elemento se desplaza hacia la derecha (para permitir agregar otro menú) y se abre otro cuadro de nuevo elemento debajo del primer menú, donde pueden agregarse otros comandos de menú.

   ![Cuadro nuevo elemento expandido](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Cuadro Nuevo elemento con el foco desplazado al escribir el nombre del nuevo menú

   > [!NOTE]
   > Para crear un solo elemento de menú en la barra de menús, establezca la **emergente** propiedad **False**.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)