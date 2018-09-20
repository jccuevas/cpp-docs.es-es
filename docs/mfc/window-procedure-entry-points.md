---
title: Puntos de entrada del procedimiento de ventana | Microsoft Docs
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
ms.openlocfilehash: c3226df51d2a83484de78d0d76c9af67e150e8eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403193"
---
# <a name="window-procedure-entry-points"></a>Puntos de entrada de procedimiento de ventana

Para proteger los procedimientos de ventana MFC, un módulo un vínculo estático con una implementación del procedimiento de ventana especial. La vinculación se produce automáticamente cuando el módulo se vincula con MFC. Este procedimiento de ventana usa la macro AFX_MANAGE_STATE para establecer correctamente el estado efectivo del módulo, a continuación, llama `AfxWndProc`, que a su vez delega en el `WindowProc` función miembro de adecuado `CWnd`-objeto derivado.

## <a name="see-also"></a>Vea también

[Administración de los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

