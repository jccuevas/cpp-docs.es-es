---
title: Constructor Mutex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7436aeb470804bd47dcc647ff0fe9a13faaae95
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444286"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex (Constructor)

Inicializa una nueva instancia de la **Mutex** clase.

## <a name="syntax"></a>Sintaxis

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Un identificador o una referencia rvalue a un identificador, para un **Mutex** objeto.

## <a name="remarks"></a>Comentarios

El primer constructor inicializa un **Mutex** objeto a partir del identificador especificado. El segundo constructor inicializa un **Mutex** el objeto en el identificador especificado y, a continuación, mueve la propiedad del mutex actual **Mutex** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Mutex (clase)](../windows/mutex-class1.md)