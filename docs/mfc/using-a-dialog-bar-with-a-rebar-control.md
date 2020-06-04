---
title: Usar una barra de cuadro de diálogo con un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: e4e786d3670ec74b734739e29aa7e3e33b5af384
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302372"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Usar una barra de cuadro de diálogo con un control Rebar

Como se mencionó en [controles rebar y bandas](../mfc/rebar-controls-and-bands.md), cada banda solo puede contener una ventana secundaria (o control). Esto puede ser una limitación si desea tener más de una ventana secundaria por banda. Una solución adecuada consiste en crear un recurso de barra de cuadro de diálogo con varios controles y, a continuación, agregar una banda Rebar (que contenga la barra de cuadro de diálogo) al control rebar.

Normalmente, si desea que la banda de la barra de diálogo parezca transparente, debe establecer el WS_EX_TRANSPARENT estilo extendido para el objeto de barra de cuadro de diálogo. Sin embargo, dado que WS_EX_TRANSPARENT tiene algunos problemas al pintar correctamente el fondo de una barra de cuadro de diálogo, deberá realizar un pequeño trabajo adicional para lograr el efecto deseado.

En el procedimiento siguiente se detallan los pasos necesarios para conseguir la transparencia sin usar el estilo extendido de WS_EX_TRANSPARENT.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Para implementar una barra de cuadro de diálogo transparente en una banda rebar

1. Mediante el [cuadro de diálogo Agregar clase](../mfc/reference/adding-an-mfc-class.md), agregue una nueva clase (por ejemplo, `CMyDlgBar`) que implemente el objeto de barra de cuadro de diálogo.

1. Agregue un controlador para el mensaje de WM_ERASEBKGND.

1. En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Agregue un controlador para el mensaje de WM_MOVE.

1. En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Los nuevos controladores simulan la transparencia de la barra de diálogo reenviando el mensaje de WM_ERASEBKGND a la ventana primaria y forzando que se vuelva a dibujar cada vez que se mueva el objeto de barra de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
