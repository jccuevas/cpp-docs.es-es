---
title: Editar propiedades de Control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65f9c648a57dc3097b044b47c00d7dcaaa7c7409
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594822"
---
# <a name="editing-control-properties"></a>Editar las propiedades del control

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Para editar las propiedades de un control o controles

1. En el cuadro de diálogo, seleccione el control que desea modificar.

   > [!NOTE]
   > Si selecciona varios controles, se pueden editar las propiedades comunes a los controles seleccionados.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), cambiar las propiedades del control.

   > [!NOTE]
   > Al establecer el **mapa de bits** propiedad para un botón, el botón de radio o el control de casilla de verificación igual a **True**, el estilo BS_BITMAP se implementa para el control. Para obtener más información, consulte [estilos de botón](../mfc/reference/styles-used-by-mfc.md#button-styles). Para obtener un ejemplo de asociación de un mapa de bits con un control, vea [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Los mapas de bits no aparecerán en el control mientras está en el **diálogo** editor de recursos.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Para deshacer los cambios realizados en las propiedades de un control

1. Asegúrese de que el control tiene el foco el **diálogo** editor.

2. Elija **deshacer** desde el **editar** menú (si el foco no está en el control, el **deshacer** comando no estará disponible).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Tutorial: uso de recursos para la localización con ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)