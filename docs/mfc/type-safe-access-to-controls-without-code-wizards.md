---
title: Acceso con seguridad de tipos a los controles sin asistentes para código | Microsoft Docs
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
ms.openlocfilehash: 2685c946b9ee1c738ee83f9413b7fd955857febb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438345"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Acceso con seguridad de tipos a los controles sin Asistentes para código

El primer enfoque para crear acceso con seguridad de tipos a los controles usa una función de miembro insertada para convertir el tipo de valor devuelto de la clase `CWnd`del `GetDlgItem` función miembro para el tipo adecuado de control de C++, como en este ejemplo:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

A continuación, puede usar esta función miembro para el control de acceso de forma segura con código similar al siguiente:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Vea también

[Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Acceso con seguridad de tipos a los controles con Asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)

