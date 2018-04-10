---
title: Introducción a COM | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a8953949e722265afabc22410174b84c017276c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-com"></a>Introducción a COM
COM es el "modelo de objetos" fundamental en qué controles ActiveX y OLE que se compilan. COM permite que un objeto exponer su funcionalidad a otros componentes y aplicaciones del host. Define cómo se expone el objeto y el funcionamiento de esta información a través de procesos y redes. COM también define el ciclo de vida del objeto.  
  
 Estos conceptos son fundamentales para COM:  
  
-   [Interfaces](../atl/interfaces-atl.md) : el mecanismo a través del cual un objeto expone su funcionalidad.  
  
-   [IUnknown](../atl/iunknown.md) : la interfaz básica en el que se basan las demás. Implementa el recuento de referencias y la interfaz consultar mecanismos ejecutando a través de COM.  
  
-   [Recuento de referencias](../atl/reference-counting.md) : la técnica por el que un objeto (o, más estrictamente, una interfaz) decide cuándo ya no se está usando y, por tanto, es libre de eliminarse a sí mismo.  
  
-   [QueryInterface](../atl/queryinterface.md) : el método usado para consultar un objeto en una interfaz determinada.  
  
-   [El cálculo de referencias](../atl/marshaling.md) : el mecanismo que permite a los objetos que se usará en el subproceso, proceso y los límites de red, lo que permite la independencia de la ubicación.  
  
-   [Agregación](../atl/aggregation.md) : una manera en que puede hacer que un objeto de usuario de otro.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)   
 [El modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363)

