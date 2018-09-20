---
title: Destruir marco Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 742ea2fedff2e4f044e46242a4152c12855ab15e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396160"
---
# <a name="destroying-frame-windows"></a>Destruir ventanas de marco

El marco de trabajo MFC administra la destrucción de ventanas, así como la creación de las ventanas asociadas con framework documentos y vistas. Si crea ventanas adicionales, usted es responsable de destruirlas.

En el marco de trabajo, cuando el usuario cierra la ventana de marco, de forma predeterminada la ventana [OnClose](../mfc/reference/cwnd-class.md#onclose) llamadas del controlador [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). La última función miembro se llama cuando se destruye la ventana de Windows es [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la [predeterminado](../mfc/reference/cwnd-class.md#default) miembro de función para realizar la limpieza de Windows y finalmente llama a la función miembro virtual [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). El [CFrameWnd](../mfc/reference/cframewnd-class.md) implementací `PostNcDestroy` elimina el objeto de ventana de C++. Nunca debería usar C++ **eliminar** operador en una ventana de marco. Utilice `DestroyWindow` en su lugar.

Cuando se cierra la ventana principal, se cierra la aplicación. Si se modifica la documentos no guardados, el marco de trabajo muestra un cuadro de mensaje para preguntar si se deben guardar los documentos y garantiza que se guardan los documentos adecuados si es necesario.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

