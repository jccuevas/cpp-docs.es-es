---
title: Funciones miembro de CWinApp que se pueden sobrecargar
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459285"
---
# <a name="overridable-cwinapp-member-functions"></a>Funciones miembro de CWinApp que se pueden sobrecargar

[CWinApp](../mfc/reference/cwinapp-class.md) proporciona varias funciones miembro que se puede invalidar (`CWinApp` reemplaza estos miembros de clase [CWinThread](../mfc/reference/cwinthread-class.md), desde el que `CWinApp` deriva):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Run](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La única `CWinApp` es la función miembro que se debe reemplazar `InitInstance`.

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
