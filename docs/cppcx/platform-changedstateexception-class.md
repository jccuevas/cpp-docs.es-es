---
title: Platform::ChangedStateException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: 749e242db37944f0c4dcbfb785028b01a0604f14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581684"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException (Clase)

Se produce cuando el estado interno de un objeto ha cambiado, invalidando de este modo los resultados del método.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Comentarios

Un ejemplo donde se produce esta excepción es cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.

Para obtener más información, consulta la clase [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)