---
title: Configuración del Control de progreso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26afdcb58a64f2d2042596349acc4496aa530468
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380014"
---
# <a name="settings-for-the-progress-control"></a>Configuración del control de progreso
La configuración básica para el control de progreso ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) es el intervalo y la posición actual. El intervalo representa toda la duración de la operación. La posición actual representa el progreso que la aplicación ha realizado para completar la operación. Los cambios realizados en el intervalo o la posición que el control de progreso vuelva a dibujarse.  
  
 De forma predeterminada, el intervalo se establece en 0 - 100 y la posición inicial se establece en 0. Para recuperar los valores del intervalo actual para el control de progreso, utilice la [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) función miembro. Para cambiar el intervalo, utilice el [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) función miembro.  
  
 Para establecer la posición, utilice [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Para recuperar la posición actual sin especificar un nuevo valor, utilice [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Por ejemplo, puede simplemente consultar el estado de la operación actual.  
  
 Para conocer los pasos de la posición actual del control de progreso, utilice [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Para establecer la cantidad de cada paso, utilice [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)  
  
## <a name="see-also"></a>Vea también  
 [Usar CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Controles](../mfc/controls-mfc.md)

