---
title: "Introducción a las clases de ventana ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 636fe8aa87b6880f5cda77fb46fc481d99d78a81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-atl-window-classes"></a>Introducción a las clases de ventana ATL
Las siguientes clases ATL están diseñadas para implementar y manipular las ventanas:  
  
-   [CWindow](../atl/reference/cwindow-class.md) le permite asociar un identificador de ventana para el `CWindow` objeto. A continuación, llame a `CWindow` métodos para manipular la ventana.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) le permite implementar una nueva ventana y procesar mensajes con un mapa de mensajes. Puede crear una ventana basada en una nueva clase Windows, superclase de una clase existente o subclase una ventana existente.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) le permite implementar modal o un cuadro de diálogo no modal y procesar los mensajes con un mapa de mensajes.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) es una clase previamente generada que implementa una ventana cuyo mapa de mensajes está contenido en otra clase. Usar `CContainedWindowT` le permite centralizar el procesamiento de mensajes en una clase.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) le permite implementar un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) le permite implementar un cuadro de diálogo modal con funcionalidad básica.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) le permite implementar una ventana que hospeda un control ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) le permite implementar una ventana que hospeda un control ActiveX con licencia.  
  
 Además de las clases de ventana específicas, ATL proporciona varias clases diseñadas para facilitar la implementación de un objeto de ventana ATL. Son las siguientes:  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) y [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporcionan un método sencillo de estandarizar los rasgos de un objeto de ventana ATL.  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana](../atl/atl-window-classes.md)

