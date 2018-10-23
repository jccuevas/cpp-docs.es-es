---
title: TLBID | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6324ec9a64a0d1c47dab8d1beee021f6c8752a96
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807983"
---
# <a name="tlbid"></a>tlbid

**Específicos de C++**

Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.

## <a name="syntax"></a>Sintaxis

```
tlbid(number)
```

### <a name="parameters"></a>Parámetros

*Número*<br/>
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)