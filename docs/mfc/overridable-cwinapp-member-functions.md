---
title: Funciones miembro de CWinApp que se pueden sobrecargar
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447267"
---
# <a name="overridable-cwinapp-member-functions"></a>Funciones miembro de CWinApp que se pueden sobrecargar

[CWinApp](../mfc/reference/cwinapp-class.md) proporciona varias funciones miembro reemplazables de clave (`CWinApp` invalida estos miembros de la clase [CWinThread](../mfc/reference/cwinthread-class.md), de la que se deriva `CWinApp`):

- [InitInstance](../mfc/initinstance-member-function.md)

- [Ejecutar](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

La única `CWinApp` función miembro que se debe invalidar es `InitInstance`.

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
