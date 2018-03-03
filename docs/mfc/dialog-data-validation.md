---
title: "Validación de datos de cuadro de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01766dd741ed87d9ac11b8858221a1bd09b0cf31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-data-validation"></a>Validación de datos de cuadro de diálogo
Puede especificar la validación además de intercambio de datos mediante una llamada a las funciones DDV, como se muestra en el ejemplo de [intercambio de datos de cuadros de diálogo](../mfc/dialog-data-exchange.md). El `DDV_MaxChars` llamada en el ejemplo se comprueba si la cadena especificada en el control de cuadro de texto no más de 20 caracteres. La función DDV suele alerta al usuario con un cuadro de mensaje si la validación se produce un error y coloca el foco en el control de proceso causante del error, por lo que el usuario puede volver a escribir los datos. Una función DDV para un control determinado debe llamarse inmediatamente después de la función DDX para el mismo control.  
  
 También puede definir sus propias rutinas DDX y DDV personalizadas. Para obtener detalles sobre este y otros aspectos de DDX y DDV, vea [Nota técnica 26](../mfc/tn026-ddx-and-ddv-routines.md).  
  
 El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) escribirá todos lo DDX y DDV llama en la asignación de datos por usted.  
  
## <a name="see-also"></a>Vea también  
 [Datos de cuadro de diálogo intercambio y validación](../mfc/dialog-data-exchange-and-validation.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md)

