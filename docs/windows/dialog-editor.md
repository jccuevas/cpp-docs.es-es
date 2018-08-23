---
title: Cuadro de diálogo Editor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39c34487941ee45f91883ed91b1faa2c93973cfe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601729"
---
# <a name="dialog-editor"></a>Editor de cuadros de diálogo

El **diálogo** editor le permite crear o editar recursos de cuadro de diálogo. Abra el editor de cuadro de diálogo haciendo doble clic en el archivo .rc de un cuadro de diálogo en el **vista de recursos** ventana (**vista** > **vista de recursos**). Tenga en cuenta que **vista de recursos** no está disponible en las ediciones Express.

Uno de los primeros pasos para crear un cuadro de diálogo nuevo (o una plantilla de cuadro de diálogo) consiste en agregar controles. En el **diálogo** editor, puede organizar los controles para ajustarse a un determinado tamaño, forma o alineación o moverlos a fin de trabajar en el cuadro de diálogo. También es fácil eliminar un control.

Es posible almacenar un cuadro de diálogo como una plantilla para poder reutilizado más adelante. También es posible alternar entre el diseño del cuadro de diálogo y la edición del código que lo implementa.

Asimismo, en el Editor de cuadros de diálogo se pueden editar las propiedades de uno o varios controles. Puede cambiar el orden de tabulación, es decir, el orden en que se obtienen los controles centrarse cuando la **ficha** se presiona la tecla o puede definir una clave de acceso (una combinación de teclas) que permite a los usuarios elegir un control mediante el teclado. Para obtener una lista de las teclas de acceso predefinidas, vea [Teclas de aceleración del Editor de cuadros de diálogo](../windows/accelerator-keys-for-the-dialog-editor.md).

El **diálogo** editor también permite usar controles personalizados, incluidos los controles ActiveX. Además, se puede editar una [vista de formulario](../mfc/reference/cformview-class.md), [vistas de registros](../data/record-views-mfc-data-access.md)o [barras de cuadro de diálogo](../mfc/dialog-bars.md).

A partir de Visual Studio 2015, puede usar el editor de cuadro de diálogo para definir diseños dinámicos, que especifican cómo los controles moverán y cambiar el tamaño cuando el usuario cambia el tamaño de un cuadro de diálogo. Para obtener más información, vea [Dynamic Layout](../mfc/dynamic-layout.md).

- [Crear un nuevo cuadro de diálogo](../windows/creating-a-new-dialog-box.md)

- [Crear un cuadro de diálogo del que los usuarios no puedan salir en tiempo de ejecución](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

- [Cambiar entre el Editor de cuadros de diálogo y el código](../windows/switching-between-dialog-box-controls-and-code.md)

- [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)

- [Agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [Probar un cuadro de diálogo](../windows/testing-a-dialog-box.md)

- [Teclas de aceleración del Editor de cuadros de diálogo](../windows/accelerator-keys-for-the-dialog-editor.md)

- [Solucionar problemas del Editor de cuadros de diálogo](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > Al usar el **diálogo** editor, en muchos casos, puede hacer clic en el botón secundario del mouse para mostrar un menú contextual de comandos usados con frecuencia.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)  
[Controles](../mfc/controls-mfc.md)  
[Clases de control](../mfc/control-classes.md)  
[Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)  
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)