---
title: _mbbtype, _mbbtype_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbbtype
- _mbbtype_l
apilocation:
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e7b9c7aed7205e6cac428a0f627525f9484afc5a
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l
Devuelve el tipo de bytes, según el byte anterior.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _mbbtype(  
   unsigned char c,  
   int type   
);  
int _mbbtype_l(  
   unsigned char c,  
   int type,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a probar.  
  
 `type`  
 El tipo de byte que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 `_mbbtype`devuelve el tipo de byte en una cadena. Esta decisión es contextual, según lo especificado por el valor de `type`, que proporciona la condición de prueba del control. `type` es el tipo del byte anterior de la cadena. Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.  
  
|Valor de `type`|Pruebas `_mbbtype` para|Valor devuelto|`c`|  
|---------------------|--------------------------|------------------|---------|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos|`_MBC_SINGLE` (0)|Un solo byte (0 x 20 - 0x7E, 0xA1 - 0xDF)|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos|`_MBC_LEAD` (1)|Byte de un carácter multibyte inicial (0 x 81 - 0x9F, 0xE0 - 0xFC)|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos.|`_MBC_ILLEGAL`<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|  
|1|Byte final válido|`_MBC_TRAIL` (2)|Byte final de juegos de caracteres multibyte (0 x 40 - 0x7E, 0 x 80 - 0xFC)|  
|1|Byte final válido|`_MBC_ILLEGAL`<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|  
  
## <a name="remarks"></a>Comentarios  
 La función `_mbbtype` determina el tipo de un byte de un carácter multibyte. Si el valor de `type` es cualquier valor excepto 1, `_mbbtype` prueba para un byte único o un byte inicial válidos de un carácter multibyte. Si el valor de `type` es 1, `_mbbtype` prueba para un byte final válido de un carácter multibyte.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. La versión `_mbbtype` de esta función usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión `_mbbtype_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbbtype` se denominaba `chkctype`. Para el código nuevo use `_mbbtype`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_mbbtype`|\<mbstring.h>|\<mbctype.h>*|  
|`_mbbtype_l`|\<mbstring.h>|\<mbctype.h>*|  
  
 \* Para las definiciones de constantes de manifiesto que se usan como valores devueltos.  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)
