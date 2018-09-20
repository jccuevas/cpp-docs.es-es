---
title: 'Cómo: cargar un recurso de cinta desde una aplicación MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1643989a96a9003847fb53de624bff12cd51cd88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434302"
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

