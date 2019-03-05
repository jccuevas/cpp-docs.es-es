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
ms.openlocfilehash: 35db009f86a0cb984f70a349a3ecdd93bfefb0f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261250"
---
# <a name="overridable-cwinapp-member-functions"></a>Funciones miembro de CWinApp que se pueden sobrecargar

[CWinApp](../mfc/reference/cwinapp-class.md) proporciona varias funciones miembro que se puede invalidar (`CWinApp` reemplaza estos miembros de clase [CWinThread](../mfc/reference/cwinthread-class.md), desde el que `CWinApp` deriva):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Run](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La única `CWinApp` es la función miembro que se debe reemplazar `InitInstance`.

## <a name="see-also"></a>Vea también

[CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md)
