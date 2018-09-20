---
title: CReBar frente a CReBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133e298cd0bc5b497fbbba47982a755afeefb2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442856"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar frente a CReBarCtrl

MFC proporciona dos clases para crear controles rebar: [CReBar](../mfc/reference/crebar-class.md) y [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (que encapsula la API del control común de Windows). `CReBar` proporciona toda la funcionalidad del control común rebar, y controla muchas de las estructuras y configuración de control comunes necesarios para usted.

`CReBarCtrl` es una clase contenedora para el control rebar Win32 y, por lo tanto, puede ser más fácil de implementar si no va a integrar el control rebar en la arquitectura MFC. Si tiene previsto usar `CReBarCtrl` e integrar el control rebar en la arquitectura de MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control rebar a MFC. Esta comunicación no es difícil; Sin embargo, es trabajo adicional que será innecesario cuando usas `CReBar`.

Visual C++ proporciona dos maneras de aprovechar las ventajas del control rebar comunes.

- Crear el control rebar con `CReBar`y, a continuación, llame a [CReBar:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) para obtener acceso a la `CReBarCtrl` funciones miembro.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` es una función de miembro insertada que proyecta el **esto** el puntero del objeto rebar. Esto significa que, en tiempo de ejecución, la llamada de función no tiene ninguna sobrecarga.

- Crear el control rebar con [CReBarCtrl](../mfc/reference/crebarctrl-class.md)del constructor.

Cualquiera de estos métodos le dará acceso a las funciones miembro del control rebar. Cuando se llama a `CReBar::GetReBarCtrl`, devuelve una referencia a un `CReBarCtrl` por lo que puede usar cualquier conjunto de funciones miembro de objeto. Consulte [CReBar](../mfc/reference/crebar-class.md) para obtener información sobre la construcción y creación de un control rebar con `CReBar`.

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

