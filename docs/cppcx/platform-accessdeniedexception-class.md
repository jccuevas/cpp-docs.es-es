---
title: Platform::AccessDeniedException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
ms.openlocfilehash: 4865492e3b5d8e4acc35e58081a226c9e66ed99f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588154"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException (Clase)

Se produce cuando se deniega el acceso a un recurso o a una característica.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable
```

### <a name="remarks"></a>Comentarios

Si obtienes esta excepción, asegúrate de que has solicitado la capacidad adecuada y de que has realizado las declaraciones necesarias en el manifiesto del paquete de tu aplicación. Para obtener más información, consulta [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)