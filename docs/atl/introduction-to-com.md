---
title: Introducción a COM | Microsoft Docs
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
ms.openlocfilehash: 0302727bba0155fe59ffa223f5e4e91ef3c122de
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754863"
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

[Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)   
[El modelo de objetos componentes](/windows/desktop/com/the-component-object-model)

