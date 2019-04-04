---
title: unsupported_feature (Clase)
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 7635f999b227d02ec7fd56296fef1b0b047abd29
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564975"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature (Clase)

La excepción que se produce cuando se usa una función no compatible.

## <a name="syntax"></a>Sintaxis

```
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[unsupported_feature (Constructor)](#unsupported_feature)|Crea una nueva instancia de la `unsupported_feature` excepción.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupportedfeature"></a>unsupported_feature

  Crea una nueva instancia de la `unsupported_feature` excepción.

### <a name="syntax"></a>Sintaxis

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Descripción del error.

### <a name="return-value"></a>Valor devuelto

Objeto `unsupported_feature`.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres**: simultaneidad

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
