---
title: "Crear cuadros de diálogo no modal | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0549f898a076b140e7b5bed23c1c1e8c60d6adba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-modeless-dialog-boxes"></a>Crear cuadros de diálogo no modales
Para un cuadro de diálogo no modal, debe proporcionar su propio constructor público en la clase de cuadro de diálogo. Para crear un cuadro de diálogo no modal, llame a su constructor público y, a continuación, llamar al objeto de cuadro de diálogo [crear](../mfc/reference/cdialog-class.md#create) función de miembro para cargar el recurso de cuadro de diálogo. Puede llamar a **crear** durante o después de la llamada al constructor. Si el recurso de cuadro de diálogo tiene la propiedad **WS_VISIBLE**, el cuadro de diálogo aparece inmediatamente. Si no es así, debe llamar a su [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

