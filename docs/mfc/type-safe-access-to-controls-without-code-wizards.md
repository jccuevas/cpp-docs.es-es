---
title: Acceso con seguridad de tipos a los controles sin Asistentes para código
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 5b4b604bf42a327edf3ac7a83dcfc42a5e0d8c54
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261120"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Acceso con seguridad de tipos a los controles sin Asistentes para código

El primer enfoque para crear acceso con seguridad de tipos a los controles usa una función de miembro insertada para convertir el tipo de valor devuelto de la clase `CWnd`del `GetDlgItem` función miembro para el tipo adecuado de control de C++, como en este ejemplo:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

A continuación, puede usar esta función miembro para el control de acceso de forma segura con código similar al siguiente:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Vea también

[Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Acceso con seguridad de tipos a los controles con Asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)
