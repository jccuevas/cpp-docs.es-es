---
title: Filtrar Cargar un recurso de cinta desde una aplicación de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289564"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Filtrar Cargar un recurso de cinta desde una aplicación de MFC

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
