---
title: Crear un Control Rebar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 263541d9dc462b067caf763fe969f3809f1daa7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-rebar-control"></a>Crear un control Rebar
[CReBarCtrl](../mfc/reference/crebarctrl-class.md) objetos deben crearse antes de que el objeto primario es visible. Esto minimiza las posibilidades de problemas de dibujo.  
  
 Por ejemplo, controles rebar (utilizados en objetos de ventana de marco) se utilizan habitualmente como ventanas principales para los controles de barra de herramientas. Por lo tanto, el elemento primario del control rebar es el objeto de ventana de marco. Dado que el objeto de ventana de marco es el elemento primario, el `OnCreate` función de miembro (del elemento primario) es un excelente lugar para crear el control rebar.  
  
 Para usar un `CReBarCtrl` de objeto, normalmente se siguen estos pasos:  
  
### <a name="to-use-a-crebarctrl-object"></a>Para utilizar un objeto CReBarCtrl  
  
1.  Construir la [CReBarCtrl](../mfc/reference/crebarctrl-class.md) objeto.  
  
2.  Llame a [crear](../mfc/reference/crebarctrl-class.md#create) para crear el control común rebar de Windows y adjuntarlo a la `CReBarCtrl` objeto Database, especificando cualquier estilo que desee.  
  
3.  Cargar un mapa de bits, con una llamada a [CBitmap:: LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), que se usará como el fondo del objeto de control rebar.  
  
4.  Crear e inicializar los objetos de ventana secundaria (barras de herramientas, controles de cuadro de diálogo etc.) se ubicará el objeto de control rebar.  
  
5.  Inicializar un **REBARBANDINFO** estructura con la información necesaria para la banda que se va a insertar.  
  
6.  Llame a [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) para insertar las ventanas secundarias existentes (como `m_wndReToolBar`) en el nuevo control rebar. Para obtener más información sobre la inserción de bandas en un control rebar existente, vea [controles y bandas Rebar](../mfc/rebar-controls-and-bands.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

