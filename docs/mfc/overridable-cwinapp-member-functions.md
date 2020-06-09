---
title: Funciones miembro de CWinApp que se pueden sobrecargar
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624015"
---
# <a name="overridable-cwinapp-member-functions"></a>Funciones miembro de CWinApp que se pueden sobrecargar

[CWinApp](reference/cwinapp-class.md) proporciona varias funciones miembro reemplazables de clave ( `CWinApp` invalida estos miembros de la clase [CWinThread](reference/cwinthread-class.md), de la que se `CWinApp` deriva):

- [InitInstance](initinstance-member-function.md)

- [Ejecutar](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

La única `CWinApp` función miembro que debe reemplazar es `InitInstance` .

## <a name="see-also"></a>Consulte también

[CWinApp: la clase Application](cwinapp-the-application-class.md)
