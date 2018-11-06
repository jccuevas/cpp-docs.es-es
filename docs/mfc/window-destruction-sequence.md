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
ms.openlocfilehash: 07312d6c7bba219cebcfa2c73a8d66c9c97ec08e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571358"
---
# <a name="window-destruction-sequence"></a>Secuencia de destrucción de ventanas

En el marco de trabajo MFC, cuando el usuario cierra la ventana de marco, de forma predeterminada la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de función para realizar la limpieza de Windows y finalmente llama a la función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementací `PostNcDestroy` elimina el objeto de ventana de C++.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Asignación y desasignación de memoria de ventana](../mfc/allocating-and-deallocating-window-memory.md)

- [Desasociar CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>Vea también

[Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)

