---
title: Controladores de cuadro de lista
ms.date: 11/04/2016
f1_keywords:
- ON_LBN_DBLCLK
- ON_LBN_ERRSPACE
- ON_LBN_SETFOCUS
- ON_LBN_SELCHANGE
- ON_LBN_KILLFOCUS
helpviewer_keywords:
- list boxes [MFC], list box handlers
- ON_LBN_KILLFOCUS
- ON_LBN_ERRSPACE
- ON_LBN_SELCHANGE
- ON_LBN_SETFOCUS
- ON_LBN_DBLCLK
ms.assetid: e4e54412-2167-436a-883b-5dcad01820b8
ms.openlocfilehash: a104e6a8b3ed40c65b704738461c083a745464b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292614"
---
# <a name="list-box-handlers"></a>Controladores de cuadro de lista

Las siguientes entradas de mapa tienen el prototipo de función correspondiente.

|Entrada de asignación|Prototipo de función|
|---------------|------------------------|
|ON_LBN_DBLCLK( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_LBN_ERRSPACE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_LBN_KILLFOCUS( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_LBN_SELCHANGE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_LBN_SETFOCUS( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|

## <a name="see-also"></a>Vea también

[Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)
