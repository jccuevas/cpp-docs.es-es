---
title: _AtlCreateWndData Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286933"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData Structure

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
