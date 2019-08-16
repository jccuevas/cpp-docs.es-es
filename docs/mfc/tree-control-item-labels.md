---
title: Etiquetas de elemento de control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: d1f7fb8b558ff4726f7787cbf355a059fbcce8b5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513379"
---
# <a name="tree-control-item-labels"></a>Etiquetas de elemento de control de árbol

Normalmente, se especifica el texto de la etiqueta de un elemento al agregarlo al control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). La `InsertItem` función miembro puede pasar una estructura [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) que define las propiedades del elemento, incluida una cadena que contiene el texto de la etiqueta. `InsertItem`tiene varias sobrecargas a las que se puede llamar con varias combinaciones de parámetros.

Un control de árbol asigna memoria para almacenar cada elemento; el texto de las etiquetas del elemento ocupa una parte importante de esta memoria. Si la aplicación mantiene una copia de las cadenas en el control de árbol, puede reducir los requisitos de memoria del control especificando el valor **LPSTR_TEXTCALLBACK** en el miembro *miembros pszText* de `TV_ITEM` o *lpszItem* en lugar de pasar cadenas reales al control de árbol. El uso de **LPSTR_TEXTCALLBACK** hace que el control de árbol recupere el texto de la etiqueta de un elemento de la aplicación cada vez que es necesario volver a dibujar el elemento. Para recuperar el texto, el control de árbol envía un mensaje de notificación [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) , que incluye la dirección de una estructura [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-tvdispinfow) . Debe responder estableciendo los miembros adecuados de la estructura incluida.

Un control de árbol utiliza la memoria asignada del montón del proceso que crea el control de árbol. El número máximo de elementos de un control de árbol se basa en la cantidad de memoria disponible en el montón. Cada elemento toma 64 bytes.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
