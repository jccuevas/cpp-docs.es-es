---
title: lock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380300"
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