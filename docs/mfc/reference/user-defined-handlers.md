---
title: Controladores definidos por el usuario
ms.date: 11/04/2016
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: f39440d333e968c236ae5ccd750cec8854cb0530
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611552"
---
# <a name="user-defined-handlers"></a>Controladores definidos por el usuario

Las entradas de asignación siguientes corresponden a los prototipos de función.

|Entrada de asignación|Prototipo de función|
|---------------|------------------------|
|ON_MESSAGE( \<message>, \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE( \<nMessageVariable>, \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE( \<message>, \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE( \<nMessageVariable>, \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|

## <a name="see-also"></a>Vea también

[Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)<br/>
[Controladores de mensajes WM_](../../mfc/reference/handlers-for-wm-messages.md)
