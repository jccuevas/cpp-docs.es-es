---
title: Introducción a COM | Documentos de Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356180"
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

