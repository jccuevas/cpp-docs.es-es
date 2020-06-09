---
title: Destruir ventanas de marco
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
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
ms.openlocfilehash: 4bc7945ecd9aee9021ce97fa3ea05f512c58fe20
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621931"
---
# <a name="destroying-frame-windows"></a>Destruir ventanas de marco

El marco de trabajo de MFC administra la destrucción de la ventana, así como la creación de las ventanas asociadas con documentos y vistas de marco. Si crea ventanas adicionales, es el responsable de destruirlas.

En el marco de trabajo, cuando el usuario cierra la ventana de marco, el controlador [OnClose](reference/cwnd-class.md#onclose) predeterminado de la ventana llama a [DestroyWindow](reference/cwnd-class.md#destroywindow). La última función miembro a la que se llama cuando se destruye la ventana de Windows es [OnNcDestroy](reference/cwnd-class.md#onncdestroy), que realiza una limpieza, llama a la función miembro [predeterminada](reference/cwnd-class.md#default) para realizar la limpieza de Windows y, por último, llama a la función miembro virtual [PostNcDestroy](reference/cwnd-class.md#postncdestroy). La implementación de [CFrameWnd](reference/cframewnd-class.md) de `PostNcDestroy` elimina el objeto de ventana de C++. Nunca debe usar el operador **Delete** de C++ en una ventana de marco. Utilice `DestroyWindow` en su lugar.

Cuando se cierra la ventana principal, la aplicación se cierra. Si hay documentos no guardados modificados, el marco de trabajo muestra un cuadro de mensaje para preguntar si se deben guardar los documentos y asegurarse de que se guardan los documentos adecuados si es necesario.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](creating-document-frame-windows.md)

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
