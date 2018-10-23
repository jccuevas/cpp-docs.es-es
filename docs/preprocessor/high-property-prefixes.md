---
title: high_property_prefixes | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3932a7632b12120e722c5f375f4387e08f1853b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809062"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Específicos de C++**

Especifica los prefijos alternativos para tres métodos de propiedad.

## <a name="syntax"></a>Sintaxis

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parámetros

*GetPrefix*<br/>
Prefijo que se usará para el `propget` métodos.

*PutPrefix*<br/>
Prefijo que se usará para el `propput` métodos.

*PutRefPrefix*<br/>
Prefijo que se usará para el `propputref` métodos.

## <a name="remarks"></a>Comentarios

De forma predeterminada, control de errores de alto nivel `propget`, `propput`, y `propputref` métodos expuestos por funciones miembro denominadas con prefijos `Get`, `Put`, y `PutRef`, respectivamente.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)