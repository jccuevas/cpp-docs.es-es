---
title: iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l
ms.date: 11/04/2016
api_name:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
ms.openlocfilehash: bc38e72818446a94a51a37b8df5c8c8582971b3f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857767"
---
# <a name="iscsym-iscsymf-__iscsym-__iswcsym-__iscsymf-__iswcsymf-_iscsym_l-_iswcsym_l-_iscsymf_l-_iswcsymf_l"></a>iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l

Determine si un entero representa un carácter que se puede usar en un identificador.

## <a name="syntax"></a>Sintaxis

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>Parameters

*c*<br/>
Entero que se va a probar. *c* debe estar en el intervalo de 0-255 para la versión de caracteres estrechos de la función.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Tanto **__iscsym** como **__iswcsym** devuelven un valor distinto de cero si *c* es una letra, un carácter de subrayado o un dígito. Tanto **__iscsymf** como **__iswcsymf** devuelven un valor distinto de cero si *c* es una letra o un carácter de subrayado. Cada una de estas rutinas devuelve 0 si *c* no cumple la condición de prueba. Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que usan la *configuración regional* que se pasa en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Notas

Estas rutinas se definen como macros, a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS. Al usar las versiones de macro de estas rutinas, los argumentos se pueden evaluar varias veces. Tenga cuidado al usar expresiones que tengan efectos secundarios en la lista de argumentos.

Por compatibilidad con versiones anteriores, **iscsym** y **iscsymf** se definen como macros solo cuando [ &#95; &#95;stdc&#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, son indefinidos.

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**iscsym**, **iscsymf**, **__iscsym**, **__iswcsym**, **__iscsymf**, **__iswcsymf**, **_iscsym_l**, **_iswcsym_l**, **_iscsymf_l**, **_iswcsymf_l**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|

Las rutinas **iscsym**, **iscsymf**, **__iscsym**, **__iswcsym**, **__iscsymf**, **__iswcsymf**, **_iscsym_l**, **_iswcsym_l**, **_iscsymf_l**y **_iswcsymf_l** son específicas de Microsoft. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
