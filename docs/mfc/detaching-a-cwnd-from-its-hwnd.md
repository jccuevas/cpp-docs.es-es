---
title: Desasociar CWnd de su HWND
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446961"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Desasociar CWnd de su HWND

Si necesita eludir la relación de`HWND` de objetos, MFC proporciona otra `CWnd` función miembro, [detach](../mfc/reference/cwnd-class.md#detach), que desconecta el C++ objeto de ventana de la ventana de Windows. Esto evita que el destructor destruya la ventana de Windows cuando se destruye el objeto.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Asignar y desasignar memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Consulte también

[Objetos de ventana](../mfc/window-objects.md)
