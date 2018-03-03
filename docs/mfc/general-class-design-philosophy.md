---
title: "Filosofía general de diseño de clase | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- designing classes [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- classes [MFC], MFC class design
- Windows API [MFC], and MFC
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c174b06b27e78ca61d2608b8e04205068ac436e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="general-class-design-philosophy"></a>Filosofía general de diseño de clases
Microsoft Windows se diseñó mucho antes de que se hizo popular del lenguaje C++. Dado que miles de aplicaciones utilizan la interfaz de programación de aplicaciones (API) de Windows del lenguaje C, se mantendrá esa interfaz en el futuro. Cualquier interfaz de Windows de C++, por tanto, debe generarse sobre la API del lenguaje C procedimientos. Esto garantiza que las aplicaciones de C++ pueda coexistir con aplicaciones de C.  
  
 La biblioteca Microsoft Foundation Class es una interfaz orientada a objetos para Windows que cumpla los siguientes objetivos de diseño:  
  
-   Reducción significativa del trabajo necesario para escribir una aplicación para Windows.  
  
-   Velocidad de ejecución es comparable a la de la API del lenguaje C.  
  
-   Sobrecarga de tamaño de código mínimo.  
  
-   Capacidad de llamar directamente a cualquier función de C de Windows.  
  
-   Conversión más fácil de las aplicaciones existentes de C a C++.  
  
-   Capacidad de aprovechar las ventajas de la base de la experiencia de programación de C-idioma de Windows existente.  
  
-   Facilitar el uso de la API de Windows con C++ que con C.  
  
-   Más fácil de utilizar pero eficaces abstracciones de complicado características como controles ActiveX, compatibilidad con la base de datos, impresión, las barras de herramientas y barras de estado.  
  
-   API de Windows es True para C++ que utiliza eficazmente características del lenguaje C++.  
  
 Para obtener más información sobre el diseño de la biblioteca MFC, vea:  
  
-   [El marco de aplicación](../mfc/application-framework.md)  
  
-   [Relación con la API del lenguaje C](../mfc/relationship-to-the-c-language-api.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

