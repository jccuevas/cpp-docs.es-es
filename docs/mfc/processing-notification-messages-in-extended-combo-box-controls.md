---
title: Procesar mensajes de notificación en controles de cuadro combinado de extendidos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ea37fb8724a6427e287f1ebef23344662dcb34
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382796"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Procesar mensajes de notificación en los controles de cuadro combinado extendido

A medida que los usuarios interactúan con el cuadro combinado extendido, el control (`CComboBoxEx`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control, se envía la notificación CBEN_BEGINEDIT.

Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.

En la lista siguiente se describen las distintas notificaciones que envía el control de cuadro combinado extendido.

- CBEN_BEGINEDIT se envía cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control.

- CBEN_DELETEITEM se envía cuando se ha eliminado un elemento.

- CBEN_DRAGBEGIN se envía cuando el usuario comienza a arrastrar la imagen del elemento que se muestra en la parte de edición del control.

- CBEN_ENDEDIT se envía cuando el usuario finaliza una operación en el cuadro de edición o selecciona un elemento de lista de desplegable del control.

- CBEN_GETDISPINFO enviado para recuperar información de visualización sobre un elemento de devolución de llamada.

- CBEN_INSERTITEM se envía cuando se ha insertado un nuevo elemento en el control.

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)

