---
title: 'Cómo: Cargar un recurso de cinta desde una aplicación MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 14ba37952d6f8849c51b36901a6bc17404f938e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515159"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Cómo: Cargar un recurso de cinta desde una aplicación MFC

Para usar el recurso de cinta en la aplicación, modifique la aplicación para cargar el recurso de cinta de opciones.

### <a name="to-load-a-ribbon-resource"></a>Para cargar un recurso de cinta

1. Declare el `Ribbon Control` objeto en el `CMainFrame` clase.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. En `CMainFrame::OnCreate`, crear e inicializar el Control de la cinta de opciones.

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

## <a name="see-also"></a>Vea también

[Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

