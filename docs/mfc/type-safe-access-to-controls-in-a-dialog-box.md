---
title: Acceso de seguridad de tipos a los controles en un cuadro de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed8a374c34eacc48e1d877e704fdc60a20f33d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422719"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Acceso con seguridad de tipos a los controles en un cuadro de diálogo

Los controles de un cuadro de diálogo puede usar las interfaces de las clases de control MFC, como por ejemplo `CListBox` y `CEdit`. Puede crear un objeto de control y asociarlo a un cuadro de diálogo. A continuación, puede obtener acceso al control a través de su interfaz de clase, llamando a las funciones miembro para operar en el control. Los métodos aquí descritos están diseñados para proporcionarle acceso con seguridad de tipos a un control. Esto es especialmente útil para controles como cuadros de edición y cuadros de lista.

Existen dos enfoques para llevar a cabo una asociación entre un control de un cuadro de diálogo y una variable de miembro de control de C++ de una clase derivada de `CDialog`:

- [Sin asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [Con asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Vea también

[Cuadros de diálogo](../mfc/dialog-boxes.md)

