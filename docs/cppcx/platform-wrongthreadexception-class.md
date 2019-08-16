---
title: Platform::WrongThreadException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: dde8c9afff6be083580042a958f59e057bc44350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396085"
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException (Clase)

Se produce cuando un subproceso llama mediante un puntero de interfaz para un objeto proxy que no pertenece al contenedor del subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulta [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="see-also"></a>Vea también

[Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)
