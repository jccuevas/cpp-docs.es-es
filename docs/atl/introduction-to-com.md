---
title: Introducción a COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 7a200a964e0cba09878929e4362385e5badd10c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492879"
---
# <a name="introduction-to-com"></a>Introducción a COM

COM es el "modelo de objetos" fundamental en qué controles ActiveX y OLE se compilan. COM permite que un objeto exponga su funcionalidad a otros componentes y aplicaciones host. Define cómo se expone el objeto y cómo funciona esta exposición entre procesos y a través de redes. COM también define el ciclo de vida del objeto.

Estos conceptos son fundamentales para COM:

- [Interfaces](../atl/interfaces-atl.md) : el mecanismo a través del cual un objeto expone su funcionalidad.

- [IUnknown](../atl/iunknown.md) : la interfaz básica que se basan las demás. Implementa el recuento de referencias y la interfaz consultando los mecanismos que se ejecuta a través de COM.

- [Recuento de referencias](../atl/reference-counting.md) , la técnica por la que un objeto (o, de forma estricta, una interfaz) decide cuando ya no se está usando y, por tanto, es gratis para quitarse.

- [QueryInterface](../atl/queryinterface.md) : el método usado para consultar un objeto para una interfaz determinada.

- [El cálculo de referencias](../atl/marshaling.md) : el mecanismo que permite a los objetos que se usará en el subproceso, proceso y límites de red, lo que permite la independencia de la ubicación.

- [Agregación](../atl/aggregation.md) : uso de una manera en que puede hacer un objeto de otro.

## <a name="see-also"></a>Vea también

[Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)<br/>
[The Component Object Model](/windows/desktop/com/the-component-object-model) [Modelo de objetos componentes (COM)]

