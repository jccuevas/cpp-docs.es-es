---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 2012ec98d8d40d60a7f12feb68bdc371e1616223
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189798"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Específicos de Microsoft**

Produce una [_com_error](../cpp/com-error-class.md) en respuesta a un error.

## <a name="syntax"></a>Sintaxis

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parámetros

*hora*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

## <a name="remarks"></a>Observaciones

**_com_raise_error**, que se define en \<comdef. h >, se puede reemplazar por una versión escrita por el usuario del mismo nombre y prototipo. Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C++. En ese caso, una versión de usuario de **_com_raise_error** podría decidir realizar un `longjmp` o mostrar un cuadro de mensaje y detenerse. La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.

También puede utilizar [_set_com_error_handler](../cpp/set-com-error-handler.md) para reemplazar la función de control de errores predeterminada.

De forma predeterminada, **_com_raise_error** se define de la siguiente manera:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comdef. h >

**Lib:** Si el **wchar_t es Native Type** (opción del compilador) es on, use omsuppw. lib o comsuppwd. lib. Si **wchar_t es el tipo nativo** está desactivado, use comsupp. lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Consulte también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
