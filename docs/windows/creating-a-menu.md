---
title: Creación de un menú (C++)
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702809"
---
# <a name="creating-a-menu-c"></a>Creación de un menú (C++)

> [!NOTE]
> El **ventana recursos** no está disponible en las ediciones Express.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-standard-menu"></a>Para crear un menú estándar

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

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Para insertar un nuevo menú entre los menús existentes

Seleccione un nombre en el menú de existentes y presione la **insertar** clave. El **nuevo elemento** cuadro se inserta antes del elemento seleccionado.

   \- o -

Haga doble clic en la barra de menús y elija **Insertar nuevo** en el menú contextual.

## <a name="to-add-commands-to-a-menu"></a>Para agregar comandos a un menú

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

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)