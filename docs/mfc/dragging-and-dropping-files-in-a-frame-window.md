---
title: Arrastrar y colocar archivos en una ventana de marco
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 34fb6ec6d57bcf8bc1cf51a3ac0c0db5203b3ffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498867"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Arrastrar y colocar archivos en una ventana de marco

La ventana de marco administra una relación con el Explorador de archivos o el Administrador de archivos.

Por agregar unos Inicializando llama en el reemplazo de la `CWinApp` función miembro `InitInstance`, tal y como se describe en [CWinApp: la clase de aplicación](../mfc/cwinapp-the-application-class.md), puede hacer que la ventana de marco abra indirectamente archivos arrastrados desde archivo El explorador o el Administrador de archivos y se coloca en la ventana de marco. Consulte [Administrador de archivos de arrastrar y colocar](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

