---
title: Usar una barra de cuadro de diálogo con un control Rebar
ms.date: 11/04/2016
f1_keywords:
- WM_EX_TRANSPARENT
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: fdef763db5085d6419f082ecd4dddca27a5b39b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554392"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Usar una barra de cuadro de diálogo con un control Rebar

Como se mencionó en [controles y bandas Rebar](../mfc/rebar-controls-and-bands.md), cada banda puede contener sólo una ventana secundaria (o control). Esto puede suponer una limitación si desea tener más de una ventana secundaria por banda. Es una solución adecuada crear un recurso de barra de cuadro de diálogo con varios controles y, a continuación, agregar una banda rebar (que contiene la barra de cuadro de diálogo) al control rebar.

Normalmente, si deseara la banda de la barra de cuadro de diálogo aparezca transparente, establecería el WS_EX_TRANSPARENT estilo para el objeto de barra de cuadro de diálogo extendido. Sin embargo, dado que WS_EX_TRANSPARENT tiene algunos problemas con correctamente pintar el fondo de una barra de cuadro de diálogo, deberá realizar un pequeño trabajo adicional para lograr el efecto deseado.

El siguiente procedimiento describe los pasos necesarios para conseguir la transparencia sin utilizar el WS_EX_TRANSPARENT estilo extendido.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Para implementar una barra de cuadro de diálogo transparente en una banda rebar

1. Mediante el [cuadro de diálogo Agregar clase](../mfc/reference/adding-an-mfc-class.md), agregue una nueva clase (por ejemplo, `CMyDlgBar`) que implementa el objeto de barra de cuadro de diálogo.

1. Agregue un controlador para el mensaje WM_ERASEBKGND.

1. En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Agregue un controlador para el mensaje WM_MOVE.

1. En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Los nuevos controladores simulan la transparencia de la barra de cuadro de diálogo reenviar el mensaje WM_ERASEBKGND a la ventana primaria y forzando a vuelve a pintar cada vez que se mueve el objeto de barra de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

