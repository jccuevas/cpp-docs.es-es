---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: dee75bf5b16b5fe5b619444f7f2736010bb42a84
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857819"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable, _set_FMA3_enable

Obtiene o establece una marca que especifica si las funciones de biblioteca de punto flotante trascendente Math usan instrucciones FMA3 en el código compilado para plataformas x64.

## <a name="syntax"></a>Sintaxis

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parameters

*flag*<br/>
Establézcalo en 1 para habilitar las implementaciones de FMA3 de las funciones de biblioteca de punto flotante de trascendente Math en plataformas x64, o en 0 para usar las implementaciones que no usan instrucciones FMA3.

## <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si las implementaciones de FMA3 de las funciones de biblioteca de punto flotante de trascendente Math están habilitadas. De lo contrario, es cero.

## <a name="remarks"></a>Notas

Utilice la función **_set_FMA3_enable** para habilitar o deshabilitar el uso de instrucciones FMA3 en las funciones de punto flotante de trascendente Math en la biblioteca CRT. El valor devuelto refleja la implementación en uso después del cambio. Si la CPU no admite instrucciones FMA3, esta función no puede habilitarlas en la biblioteca y el valor devuelto es cero. Use **_get_FMA3_enable** para obtener el estado actual de la biblioteca. De forma predeterminada, en las plataformas x64, el código de inicio de CRT detecta si la CPU admite instrucciones FMA3 y habilita o deshabilita las implementaciones de FMA3 en la biblioteca.

Dado que las implementaciones de FMA3 usan algoritmos diferentes, las pequeñas diferencias en el resultado de los cálculos pueden ser observables cuando las implementaciones de FMA3 están habilitadas o deshabilitadas, o entre equipos que no admiten FMA3. Para obtener más información, consulte [problemas de migración de punto flotante](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Requisitos de

Las funciones **_set_FMA3_enable** y **_get_FMA3_enable** solo están disponibles en las versiones x64 de CRT.

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h><br />C++: \<CMATH > o \<Math. h >|

Las funciones **_set_FMA3_enable** y **_get_FMA3_enable** son específicas de Microsoft. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad de punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Problemas de migración de punto flotante](../../porting/floating-point-migration-issues.md)<br/>
