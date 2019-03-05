---
title: Secuencia de destrucción de ventanas
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: d4592e6ac0077d6bc335b50f2d67b140402b4fe2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287666"
---
# <a name="window-destruction-sequence"></a>Secuencia de destrucción de ventanas

En el marco de trabajo MFC, cuando el usuario cierra la ventana de marco, de forma predeterminada la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de función para realizar la limpieza de Windows y finalmente llama a la función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementací `PostNcDestroy` elimina el objeto de ventana de C++.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Asignación y desasignación de memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Vea también

[Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)
