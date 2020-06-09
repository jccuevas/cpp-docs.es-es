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
ms.openlocfilehash: 02546559183d0e14973bc2e5ccb26a4570a39b1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623263"
---
# <a name="allocating-and-deallocating-window-memory"></a>Asignar y desasignar memoria de ventana

No use el operador **Delete** de C++ para destruir una ventana o vista de marco. En su lugar, llame a la `CWnd` función miembro `DestroyWindow` . Por lo tanto, las ventanas de marco deben asignarse en el montón con el operador **New**. Tenga cuidado al asignar ventanas de marco en el marco de pila o globalmente. Siempre que sea posible, se deben asignar otras ventanas en el marco de pila.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas](creating-windows.md)

- [Secuencia de destrucción de ventanas](window-destruction-sequence.md)

- [Desasociar CWnd de su HWND](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Consulte también

[Destruir objetos Window](destroying-window-objects.md)
