---
title: CReBar frente a CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445286"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar frente a CReBarCtrl

MFC proporciona dos clases para crear rebarras: [CReBar](../mfc/reference/crebar-class.md) y [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (que contiene la API de control común de Windows). `CReBar` proporciona toda la funcionalidad del control común rebar y controla muchas de las configuraciones y estructuras de control comunes necesarias.

`CReBarCtrl` es una clase contenedora para el control rebar de Win32 y, por consiguiente, puede ser más fácil de implementar si no tiene intención de integrar el rebar en la arquitectura de MFC. Si piensa usar `CReBarCtrl` e integrar el rebar en la arquitectura de MFC, debe tener cuidado adicional para comunicar las manipulaciones del control rebar a MFC. Esta comunicación no es difícil. sin embargo, se trata de un trabajo adicional que no es necesario cuando se usa `CReBar`.

Visual C++ proporciona dos maneras de aprovechar el control común de rebar.

- Cree el rebar mediante `CReBar`y, a continuación, llame a [CReBar:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) para obtener acceso a las funciones miembro de `CReBarCtrl`.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` es una función miembro insertada que convierte el puntero **this** del objeto rebar. Esto significa que, en tiempo de ejecución, la llamada de función no tiene sobrecarga.

- Cree el rebar mediante el constructor de [CReBarCtrl](../mfc/reference/crebarctrl-class.md).

Cualquier método le dará acceso a las funciones miembro del control rebar. Cuando se llama a `CReBar::GetReBarCtrl`, devuelve una referencia a un objeto `CReBarCtrl` para que pueda usar cualquier conjunto de funciones miembro. Vea [CReBar](../mfc/reference/crebar-class.md) para obtener información sobre la construcción y creación de un rebar mediante `CReBar`.

## <a name="see-also"></a>Consulte también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
