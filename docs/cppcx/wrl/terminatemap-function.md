---
title: TerminateMap (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 17d02ea9cade0301798a5d6625f8eb9a568cb2cc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785797"
---
# <a name="terminatemap-function"></a>TerminateMap (Función)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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
El nombre de un subconjunto de los generadores de clases en el módulo especificado por el parámetro *módulo*.

*forceTerminate*<br/>
**True** para terminar la clase generadores independientemente de están activos; **false** no terminar los generadores de clases si cualquier factory está activo.

## <a name="return-value"></a>Valor devuelto

**True** si todos los generadores de clases se han finalizado; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Cierra los generadores de clases en el módulo especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)