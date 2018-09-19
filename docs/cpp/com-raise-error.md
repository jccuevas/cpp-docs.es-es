---
title: _com_raise_error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dea1ac5bb15c77d1c8e0a84d2c66e3c119f01fd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031020"
---
# <a name="comraiseerror"></a>_com_raise_error

**Específicos de Microsoft**

Se produce un [_com_error](../cpp/com-error-class.md) en respuesta a un error.

## <a name="syntax"></a>Sintaxis

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parámetros

*recursos humanos*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

## <a name="remarks"></a>Comentarios

**_com_raise_error**, que se define en \<comdef.h >, se puede reemplazar por una versión escrita por el usuario del mismo nombre y prototipo. Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C++. En ese caso, una versión de usuario de **_com_raise_error** podría decidir hacer un `longjmp` o mostrar un cuadro de mensaje y detener. La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.

También puede usar [_set_com_error_handler](../cpp/set-com-error-handler.md) para reemplazar la función de control de errores de forma predeterminada.

De forma predeterminada, **_com_raise_error** se define como sigue:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comdef.h >

**Lib:** si el **wchar_t es tipo nativo** opción del compilador está activada, use omsuppw.lib o comsuppwd.lib. Si **wchar_t es tipo nativo** está desactivada, use comsupp.lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)