---
title: Funciones miembro de CWinApp reemplazable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d454ce65a2068a00f9b2c7f5934951f295738c12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347716"
---
# <a name="overridable-cwinapp-member-functions"></a>Funciones miembro de CWinApp que se pueden sobrecargar
[CWinApp](../mfc/reference/cwinapp-class.md) proporciona varias funciones miembro reemplazables (`CWinApp` reemplaza estos miembros de clase [CWinThread](../mfc/reference/cwinthread-class.md), desde el que `CWinApp` deriva):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [Run](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 El único `CWinApp` es la función de miembro que se debe reemplazar `InitInstance`.  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
