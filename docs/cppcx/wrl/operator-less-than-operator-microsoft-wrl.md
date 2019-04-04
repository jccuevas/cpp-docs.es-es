---
title: 'operador&lt; (Microsoft:: wrl)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 8b9d9936eabb75b58eabde487db8d1eb42abc9dd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785954"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operador&lt; (Microsoft:: wrl)

Determina si la dirección de un objeto es menor que otro.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Objeto izquierdo.

*b*<br/>
Objeto derecho.

## <a name="return-value"></a>Valor devuelto

**True** si la dirección de *un* es menor que la dirección de *b*; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)