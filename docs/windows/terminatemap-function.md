---
title: TerminateMap (Función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: efee7edfc1085288b3220698024cb0deeb4e71af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643227"
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
Un [módulo](../windows/module-class.md).

*Nombre de servidor*<br/>
El nombre de un subconjunto de los generadores de clases en el módulo especificado por el parámetro *módulo*.

*forceTerminate*<br/>
**True** para terminar la clase generadores independientemente de están activos; **false** no terminar los generadores de clases si cualquier factory está activo.

## <a name="return-value"></a>Valor devuelto

**True** si todos los generadores de clases se han finalizado; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Cierra los generadores de clases en el módulo especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)