---
title: Puntos de entrada de procedimiento de ventana | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1095061cce8ff8f189984aca99a06eb741a46e83
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382078"
---
# <a name="window-procedure-entry-points"></a>Puntos de entrada de procedimiento de ventana
Para proteger los procedimientos de ventana MFC, un módulo un vínculo estático con una implementación de procedimiento de ventana especial. La vinculación se produce automáticamente cuando el módulo se vincula con MFC. Este procedimiento de ventana se utiliza la `AFX_MANAGE_STATE` macro para establecer correctamente el estado efectivo del módulo, a continuación, llama **AfxWndProc**, que a su vez delega en el `WindowProc` función miembro de la correspondiente `CWnd`-derivado objeto.  
  
## <a name="see-also"></a>Vea también  
 [Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

