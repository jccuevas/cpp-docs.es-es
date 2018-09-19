---
title: Usar una barra de cuadro de diálogo con un Control Rebar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2628df5f446105e6b7881709a0c72c19fe230e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950495"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Usar una barra de cuadro de diálogo con un control Rebar
Como se mencionó en [controles y bandas Rebar](../mfc/rebar-controls-and-bands.md), cada banda puede contener solo una ventana secundaria (o control). Esto puede ser una limitación si desea tener más de una ventana secundaria por banda. Una solución adecuada consiste en crear un recurso de barra de cuadro de diálogo con varios controles y, a continuación, agregar una banda rebar (que contiene la barra de cuadro de diálogo) al control rebar.  
  
 Normalmente, si desea que la banda de la barra de cuadro de diálogo aparezca transparente, establecería el estilo extendido WM_EX_TRANSPARENT para el objeto de barra de cuadro de diálogo. Sin embargo, dado que WS_EX_TRANSPARENT tiene algunos problemas con correctamente pintar el fondo de una barra de cuadro de diálogo, debe realizar un pequeño trabajo adicional para lograr el efecto deseado.  
  
 El siguiente procedimiento describe los pasos necesarios para conseguir la transparencia sin utilizar el WS_EX_TRANSPARENT estilo extendido.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Para implementar una barra de cuadro de diálogo transparente en una banda rebar  
  
1.  Mediante el [cuadro de diálogo Agregar clase](../mfc/reference/adding-an-mfc-class.md), agregue una nueva clase (por ejemplo, `CMyDlgBar`) que implementa el objeto de barra de cuadro de diálogo.  
  
2.  Agregue un controlador para el mensaje WM_ERASEBKGND.  
  
3.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Agregue un controlador para el mensaje WM_MOVE.  
  
5.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Los nuevos controladores simulan la transparencia de la barra de cuadro de diálogo enviando el mensaje WM_ERASEBKGND a la ventana primaria y forzando a vuelva a dibujarse cada vez que se mueve el objeto de barra de cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

