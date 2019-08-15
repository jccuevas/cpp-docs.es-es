---
title: Introducción a COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: e29f761e0380357bc999af82cc4bde8bfbaf4d6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492355"
---
# <a name="introduction-to-com"></a>Introducción a COM

COM es el "modelo de objetos" fundamental en el que se compilan los controles ActiveX y OLE. COM permite que un objeto exponga su funcionalidad a otros componentes y a las aplicaciones host. Define el modo en que el objeto se expone a sí mismo y cómo funciona esta exposición entre los procesos y las redes. COM también define el ciclo de vida del objeto.

Los conceptos fundamentales de COM son los siguientes:

- [Interfaces](../atl/interfaces-atl.md) : mecanismo a través del cual un objeto expone su funcionalidad.

- [IUnknown](../atl/iunknown.md) : la interfaz básica en la que se basan todos los demás. Implementa el recuento de referencias y los mecanismos de consulta de interfaz que se ejecutan a través de COM.

- [Recuento de referencias](../atl/reference-counting.md) : la técnica por la que un objeto (o, estrictamente, una interfaz) decide cuando ya no se usa y, por lo tanto, se elimina de forma gratuita.

- [QueryInterface](../atl/queryinterface.md) : método que se usa para consultar un objeto para una interfaz determinada.

- [Serialización](../atl/marshaling.md) : mecanismo que permite usar objetos en los límites de subprocesos, procesos y redes, lo que permite la independencia de la ubicación.

- [Agregación](../atl/aggregation.md) : una manera en la que un objeto puede hacer uso de otro.

## <a name="see-also"></a>Vea también

[Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)<br/>
[The Component Object Model](/windows/win32/com/the-component-object-model) [Modelo de objetos componentes (COM)]
