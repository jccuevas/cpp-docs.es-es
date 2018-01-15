---
title: CReBar frente a CReBarCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs: C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68cd21e21c14a34122f1b26345fab767728ac6a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crebar-vs-crebarctrl"></a>CReBar frente a CReBarCtrl
MFC proporciona dos clases para crear controles rebar: [CReBar](../mfc/reference/crebar-class.md) y [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (que ajusta la API del control común de Windows). **CReBar** proporciona toda la funcionalidad del control común rebar, y controla muchas de las estructuras y configuración de control común necesaria para usted.  
  
 `CReBarCtrl`es una clase contenedora para el control rebar Win32 y, por lo tanto, puede resultar más fácil implementar si desea integrar el control rebar en la arquitectura de MFC. Si tiene previsto usar `CReBarCtrl` e integrar el control rebar en la arquitectura MFC, debe tomar precauciones adicionales para comunicar las manipulaciones del control rebar a MFC. Esta comunicación no es difícil; Sin embargo, es una tarea adicional que será innecesaria cuando usas **CReBar**.  
  
 Visual C++ proporciona dos formas de aprovechar las ventajas del control común rebar.  
  
-   Crear el control rebar mediante **CReBar**y, a continuación, llame a [CReBar:: GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) para obtener acceso a la `CReBarCtrl` funciones miembro.  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl`es una función de miembro insertada que convierte el **esto** puntero del objeto rebar. Esto significa que, en tiempo de ejecución, la llamada de función no tiene ninguna sobrecarga.  
  
-   Crear el control rebar mediante [CReBarCtrl](../mfc/reference/crebarctrl-class.md)del constructor.  
  
 Cualquier método permitirá tener acceso a las funciones miembro del control rebar. Cuando se llama a `CReBar::GetReBarCtrl`, devuelve una referencia a un `CReBarCtrl` por lo que puede utilizar cualquier conjunto de funciones miembro de objeto. Vea [CReBar](../mfc/reference/crebar-class.md) para obtener información sobre la construcción y creación de un control rebar con **CReBar**.  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

