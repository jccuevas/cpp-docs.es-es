---
title: Windows admiten las clases (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b64654f0f483ec401b379ec4c512489ce8cac823
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="windows-support-classes"></a>Clases de soporte técnico de Windows
Las clases siguientes proporcionan compatibilidad para windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) proporciona contenedores para **CreateWindow** y **CreateWindowEx**.  
  
-   [CWindow](../atl/reference/cwindow-class.md) contiene métodos para manipular una ventana. `CWindow` es la clase base de `CWindowImpl`, `CDialogImpl` y `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementa una ventana basada en una nueva clase de ventana. También le permite subclase o superclase la ventana.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementa un cuadro de diálogo.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementa un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementa un cuadro de diálogo (modal o no modal) con la funcionalidad básica.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) manipula una ventana que hospeda un control ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) proporciona métodos para manipular una ventana que hospeda un control ActiveX y también ofrece compatibilidad para hospedar controles ActiveX con licencia.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementa una ventana dentro de otro objeto.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) es compatible con el encadenamiento dinámico de mapas de mensajes.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) permite que un objeto para exponer su mensaje se asigna a otros objetos.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) proporciona un método sencillo de estandarizar los rasgos de un objeto de ventana ATL.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporciona valores predeterminados para los estilos de ventana y estilos extendidos utilizados para crear una ventana. Estos valores se agregan, mediante el operador OR lógico, para valores que se proporcionan durante la creación de una ventana.  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Clases de ventana ATL](../atl/atl-window-classes.md)  
  
 [Tutorial ATL](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)   
 [Macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md)   
 [Macros de clase de ventana](../atl/reference/window-class-macros.md)

