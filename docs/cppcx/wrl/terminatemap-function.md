---
title: TerminateMap (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 560f563e43fc8b818b04cd0bda6b01fbc916cb84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213556"
---
# <a name="terminatemap-function"></a>TerminateMap (Función)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parámetros

*module*<br/>
Un [módulo](module-class.md).

*serverName*<br/>
Nombre de un subconjunto de generadores de clase en el módulo especificado por el *módulo*de parámetros.

*forceTerminate*<br/>
**true** para finalizar los generadores de clases independientemente de que estén activos; **false** para no terminar los generadores de clase si hay algún generador activo.

## <a name="return-value"></a>Valor devuelto

**true** si todos los generadores de clases se terminaron; en caso contrario, **false**.

## <a name="remarks"></a>Observaciones

Cierra los generadores de clase en el módulo especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** Module. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
