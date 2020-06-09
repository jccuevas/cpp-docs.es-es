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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621845"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Desasociar CWnd de su HWND

Si necesita eludir la relación de objeto `HWND` , MFC proporciona otra `CWnd` función miembro, [detach](reference/cwnd-class.md#detach), que desconecta el objeto de ventana de C++ de la ventana de Windows. Esto evita que el destructor destruya la ventana de Windows cuando se destruye el objeto.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas](creating-windows.md)

- [Secuencia de destrucción de ventanas](window-destruction-sequence.md)

- [Asignar y desasignar memoria de ventana](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Consulte también

[Window (Objetos)](window-objects.md)
