---
title: lock (Clase)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 8876810b15a7d2736f2c8ab0ca1f4c6011918a5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547139"
---
# <a name="lock-class"></a>lock (Clase)

Esta clase automatiza tomar un bloqueo para sincronizar el acceso a un objeto desde varios subprocesos.  Cuando se construye adquiere el bloqueo y cuando se destruye versiones el bloqueo.

## <a name="syntax"></a>Sintaxis

```
ref class lock;
```

## <a name="remarks"></a>Comentarios

`lock` solo está disponible para los objetos de CLR y sólo puede utilizarse en el código CLR.

Internamente, los usos de la clase de bloqueo <xref:System.Threading.Monitor> para sincronizar el acceso. Vea este tema para obtener más información acerca de la sincronización.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Vea también

[lock](../dotnet/lock.md)<br/>
[lock (Miembros)](../dotnet/lock-members.md)