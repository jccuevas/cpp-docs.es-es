---
title: Acceso con seguridad de tipos a los controles sin asistentes para código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb861995c16411bb58e3051c5ffc78f75931ae8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385770"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Acceso con seguridad de tipos a los controles sin Asistentes para código
El primer enfoque para crear acceso con seguridad de tipos a los controles usa una función miembro inline para convertir el tipo de valor devuelto de la clase `CWnd`del `GetDlgItem` función de miembro para el tipo de control de C++ adecuado, como en este ejemplo:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 A continuación, puede utilizar esta función miembro para el control de acceso de un modo de seguridad de tipos con código similar al siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Acceso de seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Acceso con seguridad de tipos a los controles con Asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)

