---
title: Relación entre un objeto Window de C++ y un HWND | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b51daa375c3c920443316b6e10b6415ee018fdb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relación entre un objeto Window de C++ y un HWND
La ventana *objeto* es un objeto de C++ `CWnd` clase (o una clase derivada) que el programa crea directamente. Incluye y se quita en respuesta a las llamadas de constructor y el destructor de su programa. Las ventanas *ventana*, por otro lado, es un identificador opaco para una estructura de datos interna de Windows que corresponde a una ventana y consume recursos del sistema cuando está presente. Una ventana de Windows se identifica mediante un "identificador de ventana" (`HWND`) y se crea después la `CWnd` objeto se crea mediante una llamada a la **crear** función miembro de clase `CWnd`. Puede destruir la ventana por una llamada de programa o por una acción del usuario. El identificador de ventana se almacena en el objeto de ventana `m_hWnd` variable miembro. En la siguiente ilustración muestra la relación entre el objeto de ventana de C++ y la ventana de Windows. Creación de ventanas se describe en [crear ventanas](../mfc/creating-windows.md). Destruir ventanas se describe en [destruir objetos de ventana](../mfc/destroying-window-objects.md).  
  
 ![CWnd objeto de ventana y ventana resultante](../mfc/media/vc37fj1.gif "vc37fj1")  
Objeto de ventana y ventana de Windows  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)

