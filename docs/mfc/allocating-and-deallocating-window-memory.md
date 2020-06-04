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
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394707"
---
# <a name="allocating-and-deallocating-window-memory"></a>Asignar y desasignar memoria de ventana

No use C++ **eliminar** operador para destruir una ventana de marco o vista. En su lugar, llame a la `CWnd` función miembro `DestroyWindow`. Ventanas de marco, por lo tanto, se deben asignar en el montón con operador **nuevo**. Tenga cuidado al asignar ventanas de marco en el marco de pila o global. Otras ventanas se deben asignar en el marco de pila siempre que sea posible.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Vea también

[Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)
