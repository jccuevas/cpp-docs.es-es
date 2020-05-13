---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745084"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft Specific**

Lanza una [_com_error](../cpp/com-error-class.md) en respuesta a un error.

## <a name="syntax"></a>Sintaxis

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>Parámetros

*Hr*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

## <a name="remarks"></a>Observaciones

**_com_raise_error**, que \<se define en la> comdef.h, se puede reemplazar por una versión escrita por el usuario del mismo nombre y prototipo. Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C++. En ese caso, una **_com_raise_error** versión de `longjmp` usuario de _com_raise_error podría decidir hacer un cuadro de mensaje o mostrarlo y detenerse. La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.

También puede utilizar [_set_com_error_handler](../cpp/set-com-error-handler.md) para reemplazar la función de control de errores predeterminada.

De forma predeterminada, **_com_raise_error** se define de la siguiente manera:

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**END Microsoft Specific**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> comdef.h

**Lib:** Si la opción del compilador **wchar_t es Native Type** está activada, utilice comsuppw.lib o comsuppwd.lib. Si **wchar_t es Native Type** está desactivado, utilice comsupp.lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
