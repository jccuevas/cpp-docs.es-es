---
title: Controladores de comandos para el registro de desplazamiento (acceso a datos MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d3164cfd8a7d78191f2076637b51d96bb45f2293
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)
El [CRecordView](../mfc/reference/crecordview-class.md) clase proporciona control para los siguientes comandos estándares de comandos predeterminado:  
  
-   **ID_RECORD_MOVE_FIRST**  
  
-   **ID_RECORD_MOVE_LAST**  
  
-   **ID_RECORD_MOVE_NEXT**  
  
-   **ID_RECORD_MOVE_PREV**  
  
 El `OnMove` función miembro proporciona un control para los cuatro comandos, que se desplazan por los registros de comandos predeterminado. Cuando se emiten estos comandos, RFX (o DFX) carga el nuevo registro en los campos del conjunto de registros y DDX mueve los valores a los controles del formulario de registro. Para obtener información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Asegúrese de utilizar estos identificadores de comando estándar para todos los objetos de interfaz de usuario asociados a los comandos estándar de exploración de registros.  
  
## <a name="see-also"></a>Vea también  
 [Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)