---
title: Crear un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274468"
---
# <a name="creating-a-rebar-control"></a>Crear un control Rebar

[CReBarCtrl](../mfc/reference/crebarctrl-class.md) objetos deben crearse antes de que el objeto primario es visible. Esto minimiza las posibilidades de problemas de dibujo.

Por ejemplo, los controles rebar (utilizados en objetos de ventana de marco) normalmente se usan como ventanas principales para los controles de barra de herramientas. Por lo tanto, el elemento primario del control rebar es el objeto de ventana de marco. Dado que el objeto de ventana de marco es el elemento primario, el `OnCreate` función miembro (del elemento primario) es un lugar excelente para crear el control rebar.

Para usar un `CReBarCtrl` de objeto, normalmente se siguen estos pasos:

### <a name="to-use-a-crebarctrl-object"></a>Para utilizar un objeto CReBarCtrl

1. Construir la [CReBarCtrl](../mfc/reference/crebarctrl-class.md) objeto.

1. Llame a [crear](../mfc/reference/crebarctrl-class.md#create) para crear el control común de rebar de Windows y adjuntarlo a la `CReBarCtrl` objeto, que especifica cualquier estilo que desee.

1. Cargar un mapa de bits, con una llamada a [CBitmap:: LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), que se usará como el fondo del objeto del control rebar.

1. Crear e inicializar los objetos de ventana secundaria (barras de herramientas, controles de cuadro de diálogo etc.) que contendrá el objeto de control rebar.

1. Inicializar un **REBARBANDINFO** estructura con la información necesaria para la banda que se va a insertar.

1. Llame a [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) para insertar las ventanas secundarias existentes (como `m_wndReToolBar`) en el nuevo control rebar. Para obtener más información sobre la inserción de bandas en un control rebar existente, vea [controles y bandas Rebar](../mfc/rebar-controls-and-bands.md).

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
