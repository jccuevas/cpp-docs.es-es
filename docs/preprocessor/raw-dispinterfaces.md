---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: ef8ed3992c77df0f1d551e923ddc90c2d1bb9b0b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027928"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Específicos de C++**

Indica al compilador que genere funciones de contenedor de bajo nivel para dispinterface métodos y propiedades que llaman a `IDispatch::Invoke` y devolver el código de error HRESULT.

## <a name="syntax"></a>Sintaxis

```
raw_dispinterfaces
```

## <a name="remarks"></a>Comentarios

Si no se especifica este atributo, solo se generan los contenedores de alto nivel, que inician excepciones de C++ en caso de error.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)