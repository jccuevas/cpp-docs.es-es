---
title: Trabajar con objetos Window | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1eb8622c18a9b9539388ad2b3162916288cb28af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-window-objects"></a>Trabajar con objetos Window
Trabajar con ventanas requiere dos tipos de actividad:  
  
-   Controlar mensajes de Windows  
  
-   En la ventana de dibujo  
  
 Para controlar los mensajes de Windows en cualquier ventana, incluidas sus propias ventanas secundarias, vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para asignar los mensajes a la clase de ventana de C++. A continuación, escriba al controlador de mensajes funciones miembro en la clase.  
  
 La mayoría de dibujo en una aplicación de marco de trabajo se produce en la vista, cuyo [OnDraw](../mfc/reference/cview-class.md#ondraw) función miembro se llama cada vez que se debe dibujar el contenido de la ventana. Si la ventana es un elemento secundario de la vista, puede delegar algunas de dibujo de la vista en la ventana secundaria haciendo que `OnDraw` llamar a una de las funciones de miembro de la ventana.  
  
 En cualquier caso, necesitará un contexto de dispositivo para dibujar. Puede usar el lápiz estándar, pincel y otros objetos gráficos contenidas en el contexto de dispositivo asociado a la ventana. O bien, puede modificar estos objetos para obtener los efectos de dibujo que necesarios. Con el contexto de dispositivo configurado como sea necesario, llamar a funciones miembro de clase [CDC](../mfc/reference/cdc-class.md) (clase de contexto de dispositivo) para dibujar líneas, formas y texto; para utilizar colores; y para trabajar con un sistema de coordenadas.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos de ventana](../mfc/window-objects.md)

