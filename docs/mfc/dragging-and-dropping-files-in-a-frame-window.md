---
title: Arrastrar y colocar archivos en una ventana de marco | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc68923de531240a2d59336c79e54f6562b369c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380534"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Arrastrar y colocar archivos en una ventana de marco

La ventana de marco administra una relación con el Explorador de archivos o el Administrador de archivos.

Por agregar unos Inicializando llama en el reemplazo de la `CWinApp` función miembro `InitInstance`, tal y como se describe en [CWinApp: la clase de aplicación](../mfc/cwinapp-the-application-class.md), puede hacer que la ventana de marco abra indirectamente archivos arrastrados desde archivo El explorador o el Administrador de archivos y se coloca en la ventana de marco. Consulte [Administrador de archivos de arrastrar y colocar](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

