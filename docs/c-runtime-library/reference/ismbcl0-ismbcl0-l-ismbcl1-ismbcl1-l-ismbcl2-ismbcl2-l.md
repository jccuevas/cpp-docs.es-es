---
title: _ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcl2
- _ismbcl1
- _ismbcl0
- _ismbcl2_l
- _ismbcl1_l
- _ismbcl0_l
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
- ismbcl0
- _ismbcl1_l
- _ismbcl0
- ismbcl1
- ismbcl0_l
- _ismbcl2_l
- ismbcl2
- ismbcl1_l
- _ismbcl1
- _ismbcl0_l
- _ismbcl2
- ismbcl2_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbcl0_l function
- _ismbcl2 function
- _ismbcl1_l function
- ismbcl2 function
- _ismbcl1 function
- ismbcl0_l function
- ismbcl2_l function
- ismbcl1_l function
- ismbcl0 function
- ismbcl1 function
- _ismbcl2_l function
- _ismbcl0 function
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
caps.latest.revision: 20
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
ms.openlocfilehash: 23ae0c873ef956499c46800abebba62cb656557b
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="ismbcl0-ismbcl0l-ismbcl1-ismbcl1l-ismbcl2-ismbcl2l"></a>_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l
**Funciones concretas de la página de códigos 932**, usando la configuración regional actual o la categoría de estado de conversión LC_CTYPE especificada.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _ismbcl0(  
   unsigned int c   
);  
int _ismbcl0_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcl1(  
   unsigned int c   
);  
int _ismbcl1_l(  
   unsigned int c ,  
   _locale_t locale  
);  
int _ismbcl2(  
   unsigned int c   
);  
int _ismbcl2_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si `c` <= 255 y hay una rutina `_ismbb` correspondiente (por ejemplo, `_ismbcalnum` corresponde a `_ismbbalnum`), el resultado es el valor devuelto de la rutina `_ismbb` correspondiente.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
|Rutina|Condición de prueba (solo página de códigos 932)|  
|-------------|-------------------------------------------|  
|`_ismbcl0`|JIS no Kanji: 0x8140<=`c`<=0x889E.|  
|`_ismbcl0_l`|JIS no Kanji: 0x8140<=`c`<=0x889E.|  
|`_ismbcl1`|JIS de nivel 1: 0x889F<=`c`<=0x9872.|  
|`_ismbcl1_l`|JIS de nivel 1: 0x889F<=`c`<=0x9872.|  
|`_ismbcl2`|JIS de nivel 2: 0x989F<=`c`<=0xEAA4.|  
|`_ismbcl2_l`|JIS de nivel 2: 0x989F<=`c`<=0xEAA4.|  
  
 Las funciones comprueban que el valor de `c` especificado coincide con las condiciones de prueba descritas arriba, pero no comprueben que `c` es un carácter multibyte válido. Si el byte inferior está en los intervalos 0x00 - 0x3F, 0x7F, o 0xFD - 0xFF, estas funciones devuelven un valor distinto de cero, lo que indica que el carácter cumple la condición de prueba. Use [_ismbbtrail](../../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) para comprobar si el carácter multibyte está definido.  
  
 **Información específica de la página de códigos de fin 932**  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ismbcl0`|\<mbstring.h>|  
|`_ismbcl0_l`|\<mbstring.h>|  
|`_ismbcl1`|\<mbstring.h>|  
|`_ismbcl1_l`|\<mbstring.h>|  
|`_ismbcl2`|\<mbstring.h>|  
|`_ismbcl2_l`|\<mbstring.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [_ismbc (Rutinas)](../../c-runtime-library/ismbc-routines.md)   
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)
