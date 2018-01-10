---
title: Crear el Control de lista | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85afbe49943e06a66cf2fa914cc87f07b0fa8c52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-list-control"></a>Crear el control de lista
Cómo controlar la lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) se crea depende de si está utilizando el control directamente o utilizando la clase [CListView](../mfc/reference/clistview-class.md) en su lugar. Si usa `CListView`, el marco de trabajo construye la vista como parte de su secuencia de creación de documento/vista. Crear la vista de lista, crea el control de la lista también (los dos son lo mismo). El control se crea en la vista [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador. En este caso, el control está listo para agregar elementos a través de una llamada a [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).  
  
### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Para utilizar CListCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadro de diálogo, agregue un Control de lista para el recurso de plantilla de cuadro de diálogo. Especifique el identificador del control.  
  
2.  Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo `CListCtrl` con la propiedad del Control. Este miembro puede utilizarse para llamar a `CListCtrl` funciones miembro.  
  
3.  Utilice la ventana Propiedades para asignar funciones controladoras en la clase de cuadro de diálogo para cualquier notificación de control de lista de los mensajes necesite controlar (vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)).  
  
4.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos para el `CListCtrl`. Vea [cambiar los estilos de Control de lista](../mfc/changing-list-control-styles.md). Esto determina el tipo de "vista" obtener en el control, aunque se puede cambiar la vista más adelante.  
  
### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Para utilizar CListCtrl en una ventana de nondialog  
  
1.  Definir el control en la clase de vista o una ventana.  
  
2.  El control de llamada [crear](../mfc/reference/clistctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establezca los estilos para el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

