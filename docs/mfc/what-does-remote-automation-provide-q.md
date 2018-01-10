---
title: "¿Qué proporciona la automatización remota? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4a82b26a1e6c208a584dfd19ebfd4530b4bdf76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="what-does-remote-automation-provide"></a>¿Qué proporciona la automatización remota?
Automatización remota permite a los programas invocar `IDispatch` las implementaciones en un equipo desde otro equipo. También admite otras interfaces requeridas por la automatización, específicamente **IEnumVARIANT** compatibilidad con las colecciones. No proporciona la capacidad de distribuir otras interfaces COM (excepto **IUnknown**, evidentemente) y, al igual que la automatización regular, contiene compatibilidad con cálculo de referencias solo para esos tipos de datos compatibles con la automatización.  
  
 Este conjunto de características permite que un programa tener acceso a los métodos y propiedades, los que devuelven colecciones u otros objetos de automatización, de un objeto que se ejecuta en un nodo de red accesible incluidos. Si el equipo cliente también ejecuta el software apropiado, es posible que el servidor devuelva la llamada al cliente, con características de automatización (Esto funciona para clientes de 32 bits y 64 bits y es conceptualmente similar a los eventos, aunque no se utiliza el mismo mecanismo).  
  
 Para que una aplicación que se pueda utilizar como un servidor de automatización remota, debe implementarse como un ejecutable (es decir, como "servidor local" en lugar de como un servidor de"inproc").  
  
## <a name="see-also"></a>Vea también  
 [Dónde encaja la automatización remota](where-does-remote-automation-fit-in-q.md)   
 [Historial de DCOM](../mfc/history-of-dcom.md)
