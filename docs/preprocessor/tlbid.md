---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037946"
---
# <a name="tlbid"></a>tlbid

**Específicos de C++**

Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.

## <a name="syntax"></a>Sintaxis

```
tlbid(number)
```

### <a name="parameters"></a>Parámetros

*número*<br/>
Número de la biblioteca de tipos en `filename`.

## <a name="remarks"></a>Comentarios

Si se crean varias bibliotecas de tipos en un único archivo DLL, se pueden cargar bibliotecas distintas de la biblioteca de tipos principal mediante el uso de **tlbid**.

Por ejemplo:

```cpp
#import <MyResource.dll> tlbid(2)
```

equivale a:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)