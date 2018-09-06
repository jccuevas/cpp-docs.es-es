---
title: _AtlCreateWndData (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5751fa3c5c8bc20f287ca3c48d885fc41c60ba0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764334"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData (estructura)

Esta estructura contiene datos de la instancia de clase en código basado en ventanas en ATL.

## <a name="syntax"></a>Sintaxis

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Miembros

`m_pThis`  
El **esto** puntero usado para obtener acceso a la instancia de clase en los procedimientos de ventana.

`m_dwThreadID`  
El identificador de subproceso de la instancia actual de la clase.

`m_pNext`  
Puntero a la siguiente `_AtlCreateWndData` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

