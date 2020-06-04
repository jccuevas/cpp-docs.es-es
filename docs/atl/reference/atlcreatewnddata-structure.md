---
title: Estructura de _AtlCreateWndData
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168545"
---
# <a name="_atlcreatewnddata-structure"></a>Estructura de _AtlCreateWndData

Esta estructura contiene datos de instancia de clase en el código de ventana en ATL.

## <a name="syntax"></a>Sintaxis

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Members

`m_pThis`<br/>
Puntero **this** que se usa para obtener acceso a la instancia de clase en los procedimientos de ventana.

`m_dwThreadID`<br/>
IDENTIFICADOR del subproceso de la instancia de clase actual.

`m_pNext`<br/>
Puntero al siguiente `_AtlCreateWndData` objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)
