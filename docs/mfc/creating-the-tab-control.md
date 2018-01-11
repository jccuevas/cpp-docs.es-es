---
title: "Crear el Control de pestaña | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs: C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91349f46e577a2a433217f84d9e028139eb09c9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-tab-control"></a>Crear el control de pestaña
¿Cómo se crea el control de pestaña depende de si está usando el control en un cuadro de diálogo o crear en una ventana de nondialog.  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Para utilizar CTabCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadro de diálogo, agregue un Control de pestaña a un recurso de plantilla de cuadro de diálogo. Especifique el identificador del control.  
  
2.  Use la [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de tipo [CTabCtrl](../mfc/reference/ctabctrl-class.md) con la propiedad del Control. Este miembro puede utilizarse para llamar a `CTabCtrl` funciones miembro.  
  
3.  Asignar funciones de controlador de la clase de cuadro de diálogo para cualquier mensaje de notificación de control de ficha que necesite controlar. Para obtener más información, consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
4.  En [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), establecer los estilos para el `CTabCtrl`.  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Para utilizar CTabCtrl en una ventana de nondialog  
  
1.  Definir el control en la clase de vista o una ventana.  
  
2.  El control de llamada [crear](../mfc/reference/ctabctrl-class.md#create) función miembro, posiblemente en [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), posiblemente tan pronto como la ventana primaria [OnCreate](../mfc/reference/cwnd-class.md#oncreate) función de controlador (si es creación de subclases del control). Establezca los estilos para el control.  
  
 Después de la `CTabCtrl` ha creado un objeto, puede establecer o borrar los siguientes estilos extendidos:  
  
-   **TCS_EX_FLATSEPARATORS** el control de ficha dibujará separadores entre los elementos de ficha. Este estilo extendido sólo afecta a la ficha controles que tienen la **TCS_BUTTONS** y **TCS_FLATBUTTONS** estilos. De forma predeterminada, la creación del control de pestaña con el **TCS_FLATBUTTONS** estilo establece este estilo extendido.  
  
-   **TCS_EX_REGISTERDROP** el control de pestaña genera **TCN_GETOBJECT** mensajes de notificación para solicitar un destino de colocación de objetos cuando se arrastra un objeto sobre los elementos de ficha en el control.  
  
    > [!NOTE]
    >  Para recibir el **TCN_GETOBJECT** notificación, debe inicializar las bibliotecas OLE con una llamada a [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).  
  
 Estos estilos se pueden recuperar y establecer, después de que se ha creado el control, con llamadas a la [funciones miembro GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) y [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) funciones miembro.  
  
 Por ejemplo, establecer el **TCS_EX_FLATSEPARATORS** estilo con las siguientes líneas de código:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 Desactive el **TCS_EX_FLATSEPARATORS** de estilo de un `CTabCtrl` objeto con las siguientes líneas de código:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 Esta acción quitará los separadores que aparecen entre los botones de su `CTabCtrl` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)

