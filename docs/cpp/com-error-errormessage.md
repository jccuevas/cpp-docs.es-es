---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b1c1b5a79cdf5ee2a4a17d969d23ce0d0d85ab54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155187"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage

**Específicos de Microsoft**

Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.

## <a name="syntax"></a>Sintaxis

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el mensaje de cadena para HRESULT grabado dentro del `_com_error` objeto. Si el valor de HRESULT es un 16 bits asignado [wCode](../cpp/com-error-wcode.md), a continuación, un mensaje genérico "`IDispatch error #<wCode>`" se devuelve. Si no se encuentra ningún mensaje, se devuelve un mensaje genérico “`Unknown error #<hresult>`”. La cadena devuelta es Unicode o cadena multibyte, dependiendo del estado de la macro _UNICODE.

## <a name="remarks"></a>Comentarios

Recupera el texto del mensaje del sistema adecuado para HRESULT grabado dentro del `_com_error` objeto. El texto del mensaje del sistema se obtiene mediante una llamada a Win32 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) función. La API `FormatMessage` asigna la cadena devuelta, que se libera cuando se destruye el objeto `_com_error`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)