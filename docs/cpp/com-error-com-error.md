---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180789"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Específicos de Microsoft**

Construye un objeto de **_com_error** .

## <a name="syntax"></a>Sintaxis

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parámetros

*hora*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

*fAddRef*<br/>
El valor predeterminado hace que el constructor llame a AddRef en una interfaz de `IErrorInfo` que no sea NULL. Esto proporciona un recuento de referencias correcto en el caso común en el que la propiedad de la interfaz se pasa al objeto **_com_error** , como:

```cpp
throw _com_error(hr, perrinfo);
```

Si no desea que el código transfiera la propiedad al objeto **_com_error** , y el `AddRef` es necesario para desplazar el `Release` en el destructor **_com_error** , construya el objeto de la manera siguiente:

```cpp
_com_error err(hr, perrinfo, true);
```

*es*<br/>
Objeto de **_com_error** existente.

## <a name="remarks"></a>Observaciones

El primer constructor crea un nuevo objeto a partir de un valor HRESULT y un objeto `IErrorInfo` opcional. La segunda crea una copia de un objeto de **_com_error** existente.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error (Clase)](../cpp/com-error-class.md)
