---
title: CWinApp y el Asistente para aplicaciones MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 603504025bf4069f7a56b705e50a176975dbf244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp y el Asistente para aplicaciones MFC
Cuando crea una aplicación esqueleto, el Asistente para aplicaciones MFC declara una clase de aplicación derivada de [CWinApp](../mfc/reference/cwinapp-class.md). El Asistente para aplicaciones MFC también genera un archivo de implementación que contiene los elementos siguientes:  
  
-   Un mapa de mensajes para la clase de aplicación.  
  
-   Un constructor de clase vacía.  
  
-   Una variable que declara el único objeto de la clase.  
  
-   Una implementación estándar de su `InitInstance` función miembro.  
  
 La clase de aplicación se coloca en el encabezado del proyecto y los archivos de código fuente principal. Los nombres de la clase y los archivos creados se basan en el nombre del proyecto proporcionado por el Asistente para aplicaciones MFC. La manera más fácil de ver el código de estas clases es a través de [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Las implementaciones estándar y el mapa de mensajes suministrados son adecuados para muchos propósitos, pero puede modificarlas según sea necesario. Es el más interesante de estas implementaciones el `InitInstance` función miembro. Normalmente, agregará código a la implementación básica de `InitInstance`.  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md)   
 [Funciones miembro reemplazables de CWinApp](../mfc/overridable-cwinapp-member-functions.md)   
 [Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)

