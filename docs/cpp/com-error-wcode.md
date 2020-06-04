---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190201"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Específicos de Microsoft**

Recupera el código de error de 16 bits asignado al HRESULT encapsulado.

## <a name="syntax"></a>Sintaxis

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Valor devuelto

Si el valor HRESULT está dentro del intervalo 0x80040200 a 0x8004FFFF, el método `WCode` devuelve HRESULT menos 0x80040200; de lo contrario, devuelve cero.

## <a name="remarks"></a>Observaciones

El método `WCode` se utiliza para deshacer una asignación que tiene lugar en el código de compatibilidad con COM. El contenedor de una propiedad o método de `dispinterface` llama a una rutina de soporte que empaqueta los argumentos y llama a `IDispatch::Invoke`. Tras la devolución, si se devuelve un valor HRESULT de error de `DISP_E_EXCEPTION`, la información de error se recupera de la estructura de `EXCEPINFO` pasada a `IDispatch::Invoke`. El código de error puede ser un valor de 16 bits almacenado en el `wCode` miembro de la estructura de `EXCEPINFO` o un valor completo de 32 bits en el miembro `scode` de la estructura `EXCEPINFO`. Si se devuelve un `wCode` de 16 bits, primero se debe asignar a un valor HRESULT de error de 32 bits.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error (Clase)](../cpp/com-error-class.md)
