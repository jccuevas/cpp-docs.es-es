---
title: "Usar una barra de cuadro de diálogo con un Control Rebar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WM_EX_TRANSPARENT
dev_langs: C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd4eb47da7c3866e01ee563b9f6b42fa21ada109
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Usar una barra de cuadro de diálogo con un control Rebar
Como se mencionó en [controles y bandas Rebar](../mfc/rebar-controls-and-bands.md), cada banda puede contener solo una ventana secundaria (o control). Esto puede ser una limitación si desea tener más de una ventana secundaria por banda. Una solución adecuada consiste en crear un recurso de barra de cuadro de diálogo con varios controles y, a continuación, agregar una banda rebar (que contiene la barra de cuadro de diálogo) al control rebar.  
  
 Normalmente, si desea que la banda de la barra de cuadro de diálogo aparezca transparente, establecería la **WS_EX_TRANSPARENT** estilo para el objeto de barra de cuadro de diálogo extendido. Sin embargo, dado que **WS_EX_TRANSPARENT** tiene algunos problemas con correctamente pintar el fondo de una barra de cuadro de diálogo, debe realizar un pequeño trabajo adicional para lograr el efecto deseado.  
  
 El procedimiento siguiente detallan los pasos necesarios para conseguir la transparencia sin utilizar el **WS_EX_TRANSPARENT** estilo extendido.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Para implementar una barra de cuadro de diálogo transparente en una banda rebar  
  
1.  Mediante el [cuadro de diálogo Agregar clase](../mfc/reference/adding-an-mfc-class.md), agregue una nueva clase (por ejemplo, `CMyDlgBar`) que implementa el objeto de barra de cuadro de diálogo.  
  
2.  Agregue un controlador para el `WM_ERASEBKGND` mensaje.  
  
3.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Agregue un controlador para el `WM_MOVE` mensaje.  
  
5.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Los nuevos controladores simulan la transparencia de la barra de cuadro de diálogo mediante el reenvío de la `WM_ERASEBKGND` un mensaje a la ventana primaria y forzando que vuelva a dibujarse cada vez que se mueve el objeto de barra de cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

