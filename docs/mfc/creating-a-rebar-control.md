---
title: Crear un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 6828fa3b47eaa1e29579b09611d85cd68702c332
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617122"
---
# <a name="creating-a-rebar-control"></a>Crear un control Rebar

Los objetos [CReBarCtrl](reference/crebarctrl-class.md) deben crearse antes de que el objeto primario sea visible. Esto minimiza las posibilidades de pintar problemas.

Por ejemplo, los controles Rebar (utilizados en objetos de ventana de marco) se usan normalmente como ventanas principales para los controles de barra de herramientas. Por lo tanto, el elemento primario del control rebar es el objeto de ventana de marco. Dado que el objeto de ventana de marco es el elemento primario, la `OnCreate` función miembro (del elemento primario) es un lugar excelente para crear el control rebar.

Para usar un `CReBarCtrl` objeto, normalmente se siguen estos pasos:

### <a name="to-use-a-crebarctrl-object"></a>Para usar un objeto CReBarCtrl

1. Construya el objeto [CReBarCtrl](reference/crebarctrl-class.md) .

1. Llame a [Create](reference/crebarctrl-class.md#create) para crear el control común de rebar de Windows y adjuntarlo al `CReBarCtrl` objeto, especificando los estilos deseados.

1. Cargue un mapa de bits, con una llamada a [CBitmap:: loadBitmap](reference/cbitmap-class.md#loadbitmap), para usarlo como el fondo del objeto de control rebar.

1. Cree e inicialice los objetos de ventana secundarios (barras de herramientas, controles de cuadro de diálogo, etc.) que se incluirán en el objeto de control rebar.

1. Inicialice una estructura **REBARBANDINFO** con la información necesaria para la banda que se va a insertar.

1. Llame a [InsertBand](reference/crebarctrl-class.md#insertband) para insertar las ventanas secundarias existentes (como `m_wndReToolBar` ) en el nuevo control rebar. Para obtener más información sobre cómo insertar bandas en un control rebar existente, vea [controles y bandas rebar](rebar-controls-and-bands.md).

## <a name="see-also"></a>Consulte también

[Uso de CReBarCtrl](using-crebarctrl.md)<br/>
[Permite](controls-mfc.md)
