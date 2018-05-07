---
title: Crear el Control de encabezado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 465c880c480f9ccd3a52f6319ee97ed203c3bd74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-header-control"></a>Crear el control de encabezado
El control de encabezado no está disponible directamente en el editor de cuadro de diálogo (aunque es posible agregar un control de lista, que incluye un control de encabezado).  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>Para colocar un control de encabezado en un cuadro de diálogo  
  
1.  Incruste manualmente una variable miembro de tipo [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) en la clase de cuadro de diálogo.  
  
2.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), cree y establezca los estilos para el `CHeaderCtrl`, colocar y mostrarla.  
  
3.  Agregar elementos al control de encabezado.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de cuadro de diálogo de mensaje de cualquier notificación de control de encabezado que necesite controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Para colocar un control de encabezado en una vista (no CListView)  
  
1.  Incrustar un [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) objeto en la clase de vista.  
  
2.  Aplicar estilo, posición y mostrar la ventana de control de encabezado en la vista [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función miembro.  
  
3.  Agregar elementos al control de encabezado.  
  
4.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de vista para los mensajes de cualquier notificación de control de encabezado necesite controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
 En cualquier caso, el objeto de control incrustado se crea cuando se crea el objeto de vista o cuadro de diálogo. A continuación, debe llamar a [CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create) para crear la ventana de control. Para colocar el control, llame a [CHeaderCtrl:: Layout](../mfc/reference/cheaderctrl-class.md#layout) para determinar el tamaño inicial y la posición del control y [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) para establecer la posición que desee. A continuación, agregue elementos, como se describe en [agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).  
  
 Para obtener más información, consulte [crear un Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

