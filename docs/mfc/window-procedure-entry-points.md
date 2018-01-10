---
title: Puntos de entrada de procedimiento de ventana | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f4e99ce38bd5ae472d688dc779bdd4ccf9fd4c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="window-procedure-entry-points"></a>Puntos de entrada de procedimiento de ventana
Para proteger los procedimientos de ventana MFC, un módulo un vínculo estático con una implementación de procedimiento de ventana especial. La vinculación se produce automáticamente cuando el módulo se vincula con MFC. Este procedimiento de ventana se utiliza la `AFX_MANAGE_STATE` macro para establecer correctamente el estado efectivo del módulo, a continuación, llama **AfxWndProc**, que a su vez delega en el `WindowProc` función miembro de la correspondiente `CWnd`-derivado objeto.  
  
## <a name="see-also"></a>Vea también  
 [Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

