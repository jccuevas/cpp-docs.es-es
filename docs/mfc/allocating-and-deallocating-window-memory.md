---
title: Asignar y desasignar memoria de ventana
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: a9bbf92a586a910dfa4e81774ce4817c9cf458e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582501"
---
# <a name="allocating-and-deallocating-window-memory"></a>Asignar y desasignar memoria de ventana

No use C++ **eliminar** operador para destruir una ventana de marco o vista. En su lugar, llame a la `CWnd` función miembro `DestroyWindow`. Ventanas de marco, por lo tanto, se deben asignar en el montón con operador **nuevo**. Tenga cuidado al asignar ventanas de marco en el marco de pila o global. Otras ventanas se deben asignar en el marco de pila siempre que sea posible.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Vea también

[Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)

