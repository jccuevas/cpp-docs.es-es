---
title: UUID (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44799b507fb9c27cb1d9f166e86228ed6003a0d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086192"
---
# <a name="uuid-c"></a>uuid (C++)

**Específicos de Microsoft**

El compilador adjunta un GUID a una clase o estructura declarada o definida (COM objeto definiciones completas solo) con el **uuid** atributo.

## <a name="syntax"></a>Sintaxis

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Comentarios

El **uuid** atributo toma una cadena como su argumento. Esta cadena denomina un GUID en formato de registro normal con o sin el **{}** delimitadores. Por ejemplo:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Este atributo se puede aplicar en un nueva declaración. Esto permite que los encabezados de sistema suministren las definiciones de interfaces, como `IUnknown`y la nueva declaración en algún otro encabezado (como \<comdef.h >) para proporcionar el GUID.

La palabra clave [__uuidof](../cpp/uuidof-operator.md) se pueden aplicar para recuperar el GUID de constante asociado a un tipo definido por el usuario.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)