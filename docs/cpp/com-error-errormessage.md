---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500588"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Específicos de Microsoft**

Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.

## <a name="syntax"></a>Sintaxis

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el mensaje de cadena para el HRESULT registrado en `_com_error` el objeto. Si el valor HRESULT es un [wCode](../cpp/com-error-wcode.md)de 16 bits asignado, se devuelve un mensaje`IDispatch error #<wCode>`genérico "". Si no se encuentra ningún mensaje, se devuelve un mensaje genérico “`Unknown error #<hresult>`”. La cadena devuelta es una cadena Unicode o multibyte, dependiendo del estado de la macro _ Unicode.

## <a name="remarks"></a>Comentarios

Recupera el texto del mensaje del sistema apropiado para HRESULT registrado en `_com_error` el objeto. El texto del mensaje del sistema se obtiene mediante una llamada a la función [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) de Win32. La API `FormatMessage` asigna la cadena devuelta, que se libera cuando se destruye el objeto `_com_error`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_error (Clase)](../cpp/com-error-class.md)