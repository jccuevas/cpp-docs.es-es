---
title: Etiquetas de elemento de Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e016093e2dcde68fcc01691c4877841d648321fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207469"
---
# <a name="tree-control-item-labels"></a>Etiquetas de elemento de control de árbol
Normalmente se especifica el texto de etiqueta de un elemento cuando se agrega el elemento al control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). El `InsertItem` función miembro puede pasar un [estructura TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) estructura que define las propiedades del elemento, incluida una cadena que contiene el texto de la etiqueta. `InsertItem` tiene varias sobrecargas que se pueden llamar con distintas combinaciones de parámetros.  
  
 Un control de árbol asigna memoria para almacenar cada elemento; el texto de las etiquetas de elemento ocupa una parte importante de esta memoria. Si su aplicación mantiene una copia de las cadenas en el control de árbol, se pueden reducir los requisitos de memoria del control especificando el **LPSTR_TEXTCALLBACK** valor en el *pszText* miembro `TV_ITEM` o *lpszItem* parámetro en lugar de pasar cadenas reales al control de árbol. Uso de **LPSTR_TEXTCALLBACK** hace que el control de árbol recuperar el texto de etiqueta de un elemento de la aplicación siempre que sea necesario volver a dibujar el elemento. Para recuperar el texto, el control de árbol envía un [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) mensaje de notificación, que incluye la dirección de un [estructura NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) estructura. Debe responder estableciendo los miembros correspondientes de la estructura incluye.  
  
 Un control de árbol utiliza memoria asignada desde el montón del proceso que crea el control de árbol. El número máximo de elementos en un control de árbol se basa en la cantidad de memoria disponible en el montón. Cada elemento tiene 64 bytes.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

