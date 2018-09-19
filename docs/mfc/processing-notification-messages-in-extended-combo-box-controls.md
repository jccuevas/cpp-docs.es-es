---
title: Procesar mensajes de notificación en controles de cuadro combinado de extendidos | Documentos de Microsoft
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
ms.openlocfilehash: 576735841748d0b99053d038f8d5f674d5692f00
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930194"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Procesar mensajes de notificación en los controles de cuadro combinado extendido
A medida que los usuarios interactúan con el cuadro combinado extendido, el control (`CComboBoxEx`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control, se envía la notificación CBEN_BEGINEDIT.  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente se describen las distintas notificaciones que envía el control de cuadro combinado extendido.  
  
-   CBEN_BEGINEDIT se envía cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control.  
  
-   CBEN_DELETEITEM se envía cuando se ha eliminado un elemento.  
  
-   CBEN_DRAGBEGIN se envía cuando el usuario comienza a arrastrar la imagen del elemento mostrado en la parte de edición del control.  
  
-   CBEN_ENDEDIT se envía cuando el usuario finaliza una operación en el cuadro de edición o selecciona un elemento de la lista del control desplegable.  
  
-   CBEN_GETDISPINFO se envía para recuperar información de visualización sobre un elemento de devolución de llamada.  
  
-   CBEN_INSERTITEM se envía cuando se ha insertado un nuevo elemento en el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)

