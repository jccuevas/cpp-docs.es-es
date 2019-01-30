---
title: Editar tablas de aceleradores (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
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
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232180"
---
# <a name="editing-accelerator-tables-c"></a>Editar tablas de aceleradores (C++)

En un proyecto de C++, puede editar una tabla de aceleradores directamente con la edición en contexto en el **acelerador** editor.

Los procedimientos siguientes hacen referencia al uso de páginas de propiedades estándar, sin embargo, tanto la edición en contexto y el método de página de propiedad tienen el mismo resultado. Los cambios realizados mediante las páginas de propiedades o mediante la edición en contexto se reflejan inmediatamente en la tabla de aceleradores.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-edit-in-an-accelerator-table"></a>Para editar el contenido de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione una entrada en la tabla y seleccione esta opción para activar la edición en contexto.

1. Seleccione en el cuadro combinado desplegable o escriba para realizar cambios.

   - Para [ID](id-property.md), seleccione en la lista o escriba para editar.

   - Para [modificador](../windows/accelerator-modifier-property.md), seleccione en la lista.

   - Para [clave](../windows/accelerator-key-property.md), seleccione en la lista o escriba para editar.

   - Para [tipo](../windows/accelerator-type-property.md), seleccione **ASCII** o **VIRTKEY** en la lista.

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Para buscar una entrada en una tabla de aceleradores abierta:

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione un encabezado de columna para ordenar el contenido de la columna alfabéticamente. Por ejemplo, seleccione **ID** para mostrar alfabéticamente todos los identificadores de la tabla de aceleradores.

A continuación, puede examinar la lista y buscar la entrada.

## <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Haga doble clic en la tabla de aceleradores y elija **nuevo acelerador** desde el menú contextual, o seleccione la entrada de fila vacía en la parte inferior de la tabla.

1. Seleccione un [Id. de](id-property.md) en la lista desplegable en el Id. de cuadro o escriba un nuevo identificador en el **ID** cuadro.

1. Tipo de la [clave](../windows/accelerator-key-property.md) que desea usar como acelerador o contextual y elija **tecla siguiente** en el menú contextual para establecer una combinación de teclas (el **tecla siguiente** comando es También está disponible en el **editar** menú).

1. Cambiar el [modificador](../windows/accelerator-modifier-property.md) y [tipo](../windows/accelerator-type-property.md), si es necesario.

1. Presione **ENTRAR**.

   > [!NOTE]
   > Asegúrese de que todos los aceleradores que defina sean únicos. Puede tener varias combinaciones de teclas asignadas al mismo identificador no tiene ningún efecto negativos, por ejemplo, **Ctrl** + **P** y **F8** pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien, por ejemplo, **Ctrl** + **Z** asignado a tanto a ID_SPELL_CHECK como a ID_THESAURUS.

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>Para eliminar una entrada de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione la entrada que quiera eliminar. (Mantenga presionada la **Ctrl** o **MAYÚS** clave durante la selección para elegir varias entradas.)

1. Haga clic en y elija **eliminar** en el menú contextual (o seleccione **eliminar** desde el **editar** menú).

\- o -

- Presione el **eliminar** clave.

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Para mover o copiar una entrada de una tabla de aceleradores a otro archivo de script de recursos

1. Abra las tablas de aceleradores en los dos archivos de script de recursos.

1. Seleccione la entrada que desea mover.

1. Desde el **editar** menú, elija **copia** o **cortar**.

1. Seleccione una entrada en el archivo de script de recursos de destino.

1. Desde el **editar** menú, elija **pegar**.

   > [!NOTE]
   > También puede usar las teclas de método abreviado para copiar y pegar.

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para cambiar las propiedades de varias teclas de aceleración

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

1. Seleccione las teclas de aceleración que desee cambiar, mantenga presionada la **Ctrl** clave mientras selecciona cada uno de ellos.

1. Vaya a la [ventana propiedades](/visualstudio/ide/reference/properties-window) y escriba los valores que desea que todos los aceleradores seleccionados para compartir.

   > [!NOTE]
   > Cada valor de modificador aparece como una propiedad booleana en el **propiedades** ventana. Si cambia un [modificador](../windows/accelerator-modifier-property.md) valor en el **propiedades** ventana, la tabla de aceleradores tratará al nuevo modificador como una adición a los modificadores que previamente contenía. Por este motivo, si establece los valores de modificador, deberá establecer todos ellos para asegurarse de que todos los aceleradores compartan la misma **modificador** configuración.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de aceleradores](../windows/accelerator-editor.md)<br/>
[Editores de recursos](../windows/resource-editors.md)
