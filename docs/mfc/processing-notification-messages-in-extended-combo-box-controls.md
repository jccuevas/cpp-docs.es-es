---
title: Procesar mensajes de notificación en los controles de cuadro combinado extendido
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 58a7c5ec36807489d24014055c39775b4552be03
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620987"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Procesar mensajes de notificación en los controles de cuadro combinado extendido

A medida que los usuarios interactúan con el cuadro combinado extendido, el control (`CComboBoxEx`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control, se envía la notificación CBEN_BEGINEDIT.

Use el [Asistente para clases](reference/mfc-class-wizard.md) para agregar controladores de notificación a la clase primaria para los mensajes que desee implementar.

En la lista siguiente se describen las distintas notificaciones que envía el control de cuadro combinado extendido.

- CBEN_BEGINEDIT Se envía cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control.

- CBEN_DELETEITEM Se envía cuando se elimina un elemento.

- CBEN_DRAGBEGIN Se envía cuando el usuario comienza a arrastrar la imagen del elemento que se muestra en la parte de edición del control.

- CBEN_ENDEDIT Se envía cuando el usuario finaliza una operación en el cuadro de edición o selecciona un elemento de la lista desplegable del control.

- CBEN_GETDISPINFO Se envía para recuperar información de visualización sobre un elemento de devolución de llamada.

- CBEN_INSERTITEM Se envía cuando se inserta un nuevo elemento en el control.

## <a name="see-also"></a>Consulte también

[Uso de CComboBoxEx](using-ccomboboxex.md)<br/>
[Permite](controls-mfc.md)
