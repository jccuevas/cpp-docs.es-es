---
title: Interfaces duales y eventos | Documentos de Microsoft
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
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 87774f0237eb42c4bd2f97185230b3c869688ca8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dual-interfaces-and-events"></a>Eventos e Interfaces duales
Aunque es posible diseñar una interfaz de evento como dual, hay una serie de motivos de diseño para no hacerlo. La razón fundamental es que el origen del evento sólo desencadenará el evento a través de la vtable o `Invoke`, no ambos. Si el origen del evento desencadena el evento como una llamada de método vtable directa, la `IDispatch` métodos nunca se usará y está claro que la interfaz debería haber sido una interfaz vtable pura. Si el origen del evento desencadena el evento como una llamada a `Invoke`, nunca se usarán los métodos vtable y es que la interfaz debería haber sido una dispinterface. Si define las interfaces de eventos como duales, se necesitarán clientes para implementar parte de una interfaz que nunca se usará.  
  
> [!NOTE]
>  Este argumento no se aplica a las interfaces duales, por lo general. Desde una perspectiva de implementación, interfaces duales son una forma rápida, conveniente y ampliamente admitida de implementar las interfaces que son accesibles para una amplia gama de clientes.  
  
 Existen otros motivos para evitar interfaces duales de eventos; Visual Basic ni Internet Explorer las admiten.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)

