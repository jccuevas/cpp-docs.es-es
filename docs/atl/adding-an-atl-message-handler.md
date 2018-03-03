---
title: Agregar un controlador de mensajes ATL | Documentos de Microsoft
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
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4358dc54589971c559bec48adf77252d4f4cda28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-message-handler"></a>Agregar un controlador de mensajes ATL
Para agregar un controlador de mensajes (una función miembro que controla los mensajes de Windows) a un control, seleccione primero el control en la vista de clases. A continuación, abra el **propiedades** ventana, seleccione la **mensajes** icono y haga clic en la lista desplegable de control en el cuadro opuesto al mensaje requerido. Esto agregará una declaración para el controlador de mensajes en el archivo de encabezado del control y una implementación esqueleto del controlador en el archivo .cpp del control. También agregará el mapa de mensajes y agregue una entrada para el controlador.  
  
 Agregar un controlador de mensajes en ATL es similar a agregar un controlador de mensajes a una clase MFC. Vea [agregar un controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md) para obtener más información.  
  
 Las condiciones siguientes se aplican solo a agregar un controlador de mensajes ATL:  
  
-   Los controladores de mensajes siguen la misma convención de nomenclatura que MFC.  
  
-   Las entradas del mapa de mensajes nuevos se agregan en el mapa de mensajes principal. El asistente no reconoce los mapas de mensajes alternativos y encadenamiento de.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)

