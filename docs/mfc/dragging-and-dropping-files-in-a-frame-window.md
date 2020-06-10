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
ms.openlocfilehash: 42f21e2441f8ba3d2c6a13503c928880fe100f04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623157"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Arrastrar y colocar archivos en una ventana de marco

La ventana marco administra una relación con el explorador de archivos o el administrador de archivos.

Al agregar algunas llamadas de inicialización en la invalidación de la `CWinApp` función miembro `InitInstance` , tal como se describe en [CWinApp: la clase Application](cwinapp-the-application-class.md), puede hacer que la ventana de marco abra indirectamente los archivos arrastrados desde el explorador de archivos o el administrador de archivos y que se coloquen en la ventana de marco. Consulte [arrastrar y colocar del administrador de archivos](special-cwinapp-services.md).

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
