---
title: Agregar un controlador de mensajes ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79598b79ccbad13ad98c7fc1284808fe1b05cfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354161"
---
# <a name="adding-an-atl-message-handler"></a>Agregar un controlador de mensajes ATL
Para agregar un controlador de mensajes (una función miembro que controla los mensajes de Windows) a un control, seleccione primero el control en la vista de clases. A continuación, abra el **propiedades** ventana, seleccione la **mensajes** icono y haga clic en la lista desplegable de control en el cuadro opuesto al mensaje requerido. Esto agregará una declaración para el controlador de mensajes en el archivo de encabezado del control y una implementación esqueleto del controlador en el archivo .cpp del control. También agregará el mapa de mensajes y agregue una entrada para el controlador.  
  
 Agregar un controlador de mensajes en ATL es similar a agregar un controlador de mensajes a una clase MFC. Vea [agregar un controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md) para obtener más información.  
  
 Las condiciones siguientes se aplican solo a agregar un controlador de mensajes ATL:  
  
-   Los controladores de mensajes siguen la misma convención de nomenclatura que MFC.  
  
-   Las entradas del mapa de mensajes nuevos se agregan en el mapa de mensajes principal. El asistente no reconoce los mapas de mensajes alternativos y encadenamiento de.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)

