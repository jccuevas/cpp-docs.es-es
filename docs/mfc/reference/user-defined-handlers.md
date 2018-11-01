---
title: Controladores definidos por el usuario
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.handlers
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: 4d2102668b7cc964e6fe3bffdcc6931a2961a737
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562258"
---
# <a name="user-defined-handlers"></a>Controladores definidos por el usuario

Las entradas de asignación siguientes corresponden a los prototipos de función.

|Entrada de asignación|Prototipo de función|
|---------------|------------------------|
|ON_MESSAGE ( \<mensaje >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE ( \<mensaje >, \<memberFxn >)|afx_msg void memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|afx_msg void memberFxn (WPARAM, LPARAM);|

## <a name="see-also"></a>Vea también

[Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)<br/>
[Controladores de mensajes WM_](../../mfc/reference/handlers-for-wm-messages.md)

