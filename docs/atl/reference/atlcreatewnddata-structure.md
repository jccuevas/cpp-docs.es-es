---
title: _AtlCreateWndData (estructura)
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 860d5772279d0ca0581a8cac1e0ef224f829586d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534191"
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

`m_pThis`<br/>
El **esto** puntero usado para obtener acceso a la instancia de clase en los procedimientos de ventana.

`m_dwThreadID`<br/>
El identificador de subproceso de la instancia actual de la clase.

`m_pNext`<br/>
Puntero a la siguiente `_AtlCreateWndData` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

