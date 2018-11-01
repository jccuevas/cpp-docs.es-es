---
title: Puntos de entrada de procedimiento de ventana
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 9e395ff96d27476bc2869e23139cb2d1233f02ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500924"
---
# <a name="window-procedure-entry-points"></a>Puntos de entrada de procedimiento de ventana

Para proteger los procedimientos de ventana MFC, un módulo un vínculo estático con una implementación del procedimiento de ventana especial. La vinculación se produce automáticamente cuando el módulo se vincula con MFC. Este procedimiento de ventana usa la macro AFX_MANAGE_STATE para establecer correctamente el estado efectivo del módulo, a continuación, llama `AfxWndProc`, que a su vez delega en el `WindowProc` función miembro de adecuado `CWnd`-objeto derivado.

## <a name="see-also"></a>Vea también

[Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

