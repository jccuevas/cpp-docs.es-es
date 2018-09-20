---
title: Desasociar CWnd de su HWND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c69703d8c528d82a696fc94be76ac4a569628b4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392653"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>Desasociar CWnd de su HWND

Si tiene que evitar el objeto -`HWND` relación, MFC proporciona otra `CWnd` función miembro, [Detach](../mfc/reference/cwnd-class.md#detach), que desconecta el objeto de ventana de C++ de la ventana de Windows. Esto impide que el destructor destruir la ventana de Windows cuando se destruye el objeto.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Creación de ventanas](../mfc/creating-windows.md)

- [Secuencia de destrucción de ventanas](../mfc/window-destruction-sequence.md)

- [Asignación y desasignación de memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>Vea también

[Objetos de ventana](../mfc/window-objects.md)

