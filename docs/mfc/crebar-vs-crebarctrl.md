---
title: CReBar frente a CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 05decc095e43426044c4487b9aca05268642f915
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620455"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar frente a CReBarCtrl

MFC proporciona dos clases para crear rebarras: [CReBar](reference/crebar-class.md) y [CReBarCtrl](reference/crebarctrl-class.md) (que contiene la API de control común de Windows). `CReBar`proporciona toda la funcionalidad del control común rebar y controla muchas de las configuraciones y estructuras de control comunes necesarias.

`CReBarCtrl`es una clase contenedora para el control rebar de Win32 y, por consiguiente, puede ser más fácil de implementar si no se pretende integrar el rebar en la arquitectura de MFC. Si tiene previsto utilizar `CReBarCtrl` e integrar el rebar en la arquitectura de MFC, debe tener cuidado adicional para comunicar las manipulaciones del control rebar a MFC. Esta comunicación no es difícil. sin embargo, es un trabajo adicional que no es necesario cuando se usa `CReBar` .

Visual C++ proporciona dos maneras de aprovechar el control común de rebar.

- Cree el rebar usando `CReBar` y, a continuación, llame a [CReBar:: GetReBarCtrl](reference/crebar-class.md#getrebarctrl) para obtener acceso a las `CReBarCtrl` funciones miembro.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl`es una función miembro insertada que convierte el puntero **this** del objeto rebar. Esto significa que, en tiempo de ejecución, la llamada de función no tiene sobrecarga.

- Cree el rebar mediante el constructor de [CReBarCtrl](reference/crebarctrl-class.md).

Cualquier método le dará acceso a las funciones miembro del control rebar. Cuando se llama `CReBar::GetReBarCtrl` a, devuelve una referencia a un `CReBarCtrl` objeto, por lo que puede usar cualquier conjunto de funciones miembro. Vea [CReBar](reference/crebar-class.md) para obtener información sobre la construcción y creación de un rebar mediante `CReBar` .

## <a name="see-also"></a>Consulte también

[Uso de CReBarCtrl](using-crebarctrl.md)<br/>
[Permite](controls-mfc.md)
