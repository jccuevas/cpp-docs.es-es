---
title: Creación de un cuadro de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742653"
---
# <a name="creating-a-dialog-box-c"></a>Creación de un cuadro de diálogo (C++)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>Para crear un nuevo cuadro de diálogo

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Agregar recurso** en el menú contextual.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **Agregar recurso** cuadro de diálogo, seleccione **diálogo** en el **tipo de recurso** lista y luego elija **New**.

   Si un signo más (**+**) aparece junto a la **diálogo** tipo de recurso, significa que están disponibles plantillas de cuadro de diálogo. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

   Se abre el cuadro de diálogo nuevo en el **diálogo** editor.

   También puede [abrir cuadros de diálogo existentes en el editor de cuadro de diálogo para editar](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Para crear un cuadro de diálogo que un usuario no puedan salir

Puede crear un cuadro de diálogo en tiempo de ejecución que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.

1. En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.

   Esta configuración deshabilita el menú de sistema del cuadro de diálogo y **cerrar** botón.

1. En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .

   En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.

Para habilitar la comprobación de este tipo de cuadro de diálogo, la función de cuadro de diálogo de prueba detecta cuando **Esc** está presionado. (**Esc** es también conocida como tecla virtual VK_ESCAPE.) Independientemente de cómo el cuadro de diálogo está diseñado para comportarse en tiempo de ejecución, puede finalizar el modo de prueba presionando **Esc**.

> [!NOTE]
> Para aplicaciones MFC, para crear un cuadro de diálogo que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando  **Escriba** o **Esc**.

Para obtener información acerca de cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Cómo: Crear un recurso](../windows/how-to-create-a-resource.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)