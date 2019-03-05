---
title: Acceso con seguridad de tipos a los controles en un cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
ms.openlocfilehash: 9b8e5aef61d1a7c7277f2a6bd37b81bd156bb837
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264162"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Acceso con seguridad de tipos a los controles en un cuadro de diálogo

Los controles de un cuadro de diálogo puede usar las interfaces de las clases de control MFC, como por ejemplo `CListBox` y `CEdit`. Puede crear un objeto de control y asociarlo a un cuadro de diálogo. A continuación, puede obtener acceso al control a través de su interfaz de clase, llamando a las funciones miembro para operar en el control. Los métodos aquí descritos están diseñados para proporcionarle acceso con seguridad de tipos a un control. Esto es especialmente útil para controles como cuadros de edición y cuadros de lista.

Existen dos enfoques para llevar a cabo una asociación entre un control de un cuadro de diálogo y una variable de miembro de control de C++ de una clase derivada de `CDialog`:

- [Sin asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [Con asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)
