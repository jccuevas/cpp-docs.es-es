---
title: "Procesar mensajes de notificación en controles de cuadro combinado de extendidos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a78e7b9fd8f9c67f14a4bb51088866785d372cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Procesar mensajes de notificación en los controles de cuadro combinado extendido
A medida que los usuarios interactúan con el cuadro combinado extendido, el control (`CComboBoxEx`) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control, se envía la notificación **CBEN_BEGINEDIT** .  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente se describen las distintas notificaciones que envía el control de cuadro combinado extendido.  
  
-   **CBEN_BEGINEDIT** Se envía cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control.  
  
-   **CBEN_DELETEITEM** Se envía cuando se elimina un elemento.  
  
-   **CBEN_DRAGBEGIN** Se envía cuando el usuario comienza a arrastrar la imagen del elemento que se muestra en la parte de edición del control.  
  
-   **CBEN_ENDEDIT** Se envía cuando el usuario finaliza una operación en el cuadro de edición o selecciona un elemento de la lista desplegable del control.  
  
-   **CBEN_GETDISPINFO** Se envía para recuperar información de visualización sobre un elemento de devolución de llamada.  
  
-   **CBEN_INSERTITEM** Se envía cuando se inserta un nuevo elemento en el control.  
  
## <a name="see-also"></a>Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)

