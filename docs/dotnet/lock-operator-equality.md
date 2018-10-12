---
title: Lock::operator == | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
dev_langs:
- C++
helpviewer_keywords:
- lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7579c7493cd05d3cf2a0a119e601dd63ed5faf91
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162248"
---
# <a name="lockoperator"></a>lock::operator==

Operador de igualdad.

## <a name="syntax"></a>Sintaxis

```
template<class T> bool operator==(
   T t
);
```

#### <a name="parameters"></a>Parámetros

*t*<br/>
El objeto para comparar la igualdad.

## <a name="return-value"></a>Valor devuelto

Devuelve **true** si `t` es el mismo que el objeto de bloqueo, **false** en caso contrario.

## <a name="example"></a>Ejemplo

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Vea también

[lock (Miembros)](../dotnet/lock-members.md)<br/>
[lock::operator!=](../dotnet/lock-operator-inequality.md)