---
title: Puntos de entrada de procedimiento de ventana
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 6d91e2c432588afc5a84f7189fa87a7fc2531b1a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288651"
---
# <a name="window-procedure-entry-points"></a>Puntos de entrada de procedimiento de ventana

Para proteger los procedimientos de ventana MFC, un módulo un vínculo estático con una implementación del procedimiento de ventana especial. La vinculación se produce automáticamente cuando el módulo se vincula con MFC. Este procedimiento de ventana usa la macro AFX_MANAGE_STATE para establecer correctamente el estado efectivo del módulo, a continuación, llama `AfxWndProc`, que a su vez delega en el `WindowProc` función miembro de adecuado `CWnd`-objeto derivado.

## <a name="see-also"></a>Vea también

[Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
