---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631743"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Específicos de Microsoft**

Construye un **_com_error** objeto.

## <a name="syntax"></a>Sintaxis

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parámetros

*recursos humanos*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

*fAddRef*<br/>
El valor predeterminado hace que el constructor llame a AddRef en un valor no null `IErrorInfo` interfaz. Esto proporciona para referencia correcta de recuento en el caso habitual donde la propiedad de la interfaz se pasa a la **_com_error** objetos, como:

```cpp
throw _com_error(hr, perrinfo);
```

Si no desea que su código para transferir la propiedad a la **_com_error** objeto y el `AddRef` es necesario para desplazar el `Release` en el **_com_error** destructor, construya el objeto como se indica a continuación:

```cpp
_com_error err(hr, perrinfo, true);
```

*que*<br/>
Existente **_com_error** objeto.

## <a name="remarks"></a>Comentarios

El primer constructor crea un nuevo objeto, dados un HRESULT y opcional `IErrorInfo` objeto. El segundo crea una copia de una existente **_com_error** objeto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)