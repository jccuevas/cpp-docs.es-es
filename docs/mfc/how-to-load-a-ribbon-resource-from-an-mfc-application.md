---
title: 'Cómo: Cargar un recurso de cinta desde una aplicación MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 47a3b94bbcb14c6c2923524db1f6a83b687e50e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626406"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Cómo: Cargar un recurso de cinta desde una aplicación MFC

Para usar el recurso de la cinta de opciones en la aplicación, modifique la aplicación para cargar el recurso de la cinta de opciones.

### <a name="to-load-a-ribbon-resource"></a>Para cargar un recurso de cinta de opciones

1. Declare el `Ribbon Control` objeto en la `CMainFrame` clase.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. En `CMainFrame::OnCreate` , cree e inicialice el control de la cinta de opciones.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>Consulte también

[Diseñador de la cinta de opciones (MFC)](ribbon-designer-mfc.md)
