---
title: "Secuencia de creación de ventanas general | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59bed4387a6b8e6edeb504e29d221e76a0b39d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="general-window-creation-sequence"></a>Secuencia de creación de ventanas general
Cuando se crea una ventana de la ventana de su elección, como un elemento secundario, el marco de trabajo usa mucho el mismo proceso que se describe en [creación de documento/vista](../mfc/document-view-creation.md).  
  
 Todas las clases de ventana proporcionadas por emplean MFC [construcción en dos fases](../mfc/one-stage-and-two-stage-construction-of-objects.md). Es decir, durante una llamada de C++ **nueva** operador, el constructor asigna y se inicializa un objeto de C++ pero no crea una ventana de Windows correspondiente. Que se realiza más adelante llamando a la [crear](../mfc/reference/cwnd-class.md#create) función de miembro del objeto de ventana.  
  
 El **crear** función miembro hace que la ventana de Windows y almacena su `HWND` en miembro de datos públicos del objeto de C++ [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). **Crear** proporciona una flexibilidad completa sobre los parámetros de creación. Antes de llamar a **crear**, puede que desee registrar una clase de ventana con la función global [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) para establecer los estilos de icono y de clase para el marco.  
  
 Para ventanas de marco, puede usar el [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) función miembro en lugar de **crear**. `LoadFrame`hace que la ventana de Windows con menos parámetros. Obtiene muchos valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús.  
  
> [!NOTE]
>  El icono, tabla de aceleradores y recursos de menú deben tener un identificador de recursos comunes, como **IDR_MAINFRAME**, para que se puedan cargar mediante LoadFrame.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Window (objetos)](../mfc/window-objects.md)  
  
-   [Registrar clases de ventana""](../mfc/registering-window-classes.md)  
  
-   [Destruir objetos window](../mfc/destroying-window-objects.md)  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Vea también  
 [Creación de ventanas](../mfc/creating-windows.md)

