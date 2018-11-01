---
title: Desasociar CWnd de su HWND
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: fe4d9efa6adcec51d5944755e4a8abb1cc0784e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653978"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Desasociar CWnd de su HWND

Si tiene que evitar el objeto -`HWND` relación, MFC proporciona otra `CWnd` función miembro, [Detach](../mfc/reference/cwnd-class.md#detach), que desconecta el objeto de ventana de C++ de la ventana de Windows. Esto impide que el destructor destruir la ventana de Windows cuando se destruye el objeto.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Asignación y desasignación de memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)

