---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: 09e40d38382bea0f902fda03d15d24e0cf1a627d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187809"
---
# <a name="uuid-c"></a>uuid (C++)

**Específicos de Microsoft**

El compilador asocia un GUID a una clase o estructura declarada o definida (solo definiciones de objeto COM completo) con el atributo **UUID** .

## <a name="syntax"></a>Sintaxis

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Observaciones

El atributo **UUID** toma una cadena como argumento. Esta cadena denomina un GUID en formato de registro normal con o sin los delimitadores **{}** . Por ejemplo:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Este atributo se puede aplicar en un nueva declaración. Esto permite que los encabezados del sistema suministren las definiciones de interfaces como `IUnknown`y la nueva declaración en otro encabezado (como \<comdef. h >) para proporcionar el GUID.

La palabra clave [__uuidof](../cpp/uuidof-operator.md) se puede aplicar para recuperar el GUID de constante asociado a un tipo definido por el usuario.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
