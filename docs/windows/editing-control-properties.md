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
- dialog box controls [C++], editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f136b742d743fb359c4bb38640bd449e0e336af
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316918"
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

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)