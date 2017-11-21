---
title: Editar propiedades de Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d69f7f22b2bf3e51e2afa2ed53b04aeefe6a59e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="editing-control-properties"></a>Editar las propiedades del control
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Para editar las propiedades de un control o controles  
  
1.  En el cuadro de diálogo, seleccione el control que desea modificar.  
  
    > [!NOTE]
    >  Si selecciona varios controles, pueden modificarse únicamente las propiedades comunes a los controles seleccionados.  
  
2.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), cambiar las propiedades del control.  
  
    > [!NOTE]
    >  Al establecer el **mapa de bits** propiedad de un botón, el botón de radio o el control de casilla de verificación igual que **True**, implementa el estilo BS_BITMAP es para el control. Para obtener más información, consulte [estilos de botón](../mfc/reference/styles-used-by-mfc.md#button-styles). Para obtener un ejemplo de un mapa de bits se asocia con un control, vea [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Mapas de bits no aparecerán en el control mientras se encuentre en el editor de recursos de cuadro de diálogo.  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Para deshacer los cambios en las propiedades de un control  
  
1.  Asegúrese de que el control tiene el foco en el editor de cuadro de diálogo.  
  
2.  Elija **deshacer** desde el **editar** menú (si el foco no está en el control, el **deshacer** comando no estará disponible).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* . Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)

