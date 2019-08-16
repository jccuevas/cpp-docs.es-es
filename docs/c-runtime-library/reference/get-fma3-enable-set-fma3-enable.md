---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332200"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable, _set_FMA3_enable

Obtiene o establece una marca que especifica si las funciones de la biblioteca de punto flotante transcendentales usan instrucciones de FMA3 en el código compilado para X64 plataformas.

## <a name="syntax"></a>Sintaxis

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parámetros

*flag*<br/>
Establézcalo en 1 para habilitar las implementaciones de FMA3 de las funciones de punto flotante biblioteca math transcendentales en X64 plataformas, o 0 para usar las implementaciones que no usan instrucciones de FMA3.

## <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si se habilitan las implementaciones de FMA3 de las funciones transcendentales de la biblioteca de punto flotante. En caso contrario, es cero.

## <a name="remarks"></a>Comentarios

Utilice la **_set_FMA3_enable** función para habilitar o deshabilitar el uso de instrucciones de FMA3 en las funciones de punto flotante transcendentales matemáticas en la biblioteca CRT. El valor devuelto refleja la implementación en uso después del cambio. Si la CPU no es compatible con las instrucciones de FMA3, esta función no puede habilitar en la biblioteca y el valor devuelto es cero. Use **_get_FMA3_enable** para obtener el estado actual de la biblioteca. De forma predeterminada, en X64 plataformas, el código de inicio de CRT detecta si la CPU admite las instrucciones de FMA3 y habilita o deshabilita las implementaciones de FMA3 en la biblioteca.

Dado que las implementaciones de FMA3 usan distintos algoritmos, ligeras diferencias en el resultado de cálculos pueden ser observable cuando están habilitadas o deshabilitadas las implementaciones de FMA3, o entre equipos que o no admiten FMA3. Para obtener más información, consulte [problemas de migración de punto flotante](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Requisitos

El **_set_FMA3_enable** y **_get_FMA3_enable** funciones sólo están disponibles en el X64 versiones de CRT.

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h><br />C++: \<cmath > o \<math.h >|

El **_set_FMA3_enable** y **_get_FMA3_enable** funciones son específicas de Microsoft. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad de punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Problemas de migración de punto flotante](../../porting/floating-point-migration-issues.md)<br/>
