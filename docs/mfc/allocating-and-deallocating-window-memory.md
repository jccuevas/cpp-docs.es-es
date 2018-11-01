---
title: Asignación y desasignación de memoria de ventana | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 149a8e860913515551fc85be9b49675856d7e129
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415203"
---
# <a name="allocating-and-deallocating-window-memory"></a>Asignar y desasignar memoria de ventana

No use C++ **eliminar** operador para destruir una ventana de marco o vista. En su lugar, llame a la `CWnd` función miembro `DestroyWindow`. Ventanas de marco, por lo tanto, se deben asignar en el montón con operador **nuevo**. Tenga cuidado al asignar ventanas de marco en el marco de pila o global. Otras ventanas se deben asignar en el marco de pila siempre que sea posible.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Vea también

[Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)

