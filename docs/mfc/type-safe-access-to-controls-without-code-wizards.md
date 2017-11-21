---
title: "Acceso con seguridad de tipos a los controles sin asistentes para código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50206ec8196247deb4a63f7ac2685eed47fab5bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Acceso con seguridad de tipos a los controles sin Asistentes para código
El primer enfoque para crear acceso con seguridad de tipos a los controles usa una función miembro inline para convertir el tipo de valor devuelto de la clase `CWnd`del `GetDlgItem` función de miembro para el tipo de control de C++ adecuado, como en este ejemplo:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 A continuación, puede utilizar esta función miembro para el control de acceso de un modo de seguridad de tipos con código similar al siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Acceso de seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Acceso con seguridad de tipos a los controles con Asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)

