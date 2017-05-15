---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- _ismbcupper
- _ismbclower
dev_langs:
- C++
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 19
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 2d62b6859490047796d66cc2b56090a130ffd5f9
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
Comprueba si un carácter multibyte es una minúscula o una mayúscula.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si `c`<= 255 y hay una rutina `_ismbb` correspondiente (por ejemplo, `_ismbcalnum` corresponde a `_ismbbalnum`), el resultado es el valor devuelto de la rutina `_ismbb` correspondiente.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|  
|-------------|--------------------|---------------------------|  
|`_ismbclower`|Alfabético en minúscula|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa minúscula ASCII: 0x61<=`c`<=0x7A.|  
|`_ismbclower_l`|Alfabético en minúscula|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa minúscula ASCII: 0x61<=`c`<=0x7A.|  
|`_ismbcupper`|Alfabético en mayúscula|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa mayúscula ASCII: 0x41<=`c`<=0x5A.|  
|`_ismbcupper_l`|Alfabético en mayúscula|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa mayúscula ASCII: 0x41<=`c`<=0x5A.|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ismbclower`|\<mbstring.h>|  
|`_ismbclower_l`|\<mbstring.h>|  
|`_ismbcupper`|\<mbstring.h>|  
|`_ismbcupper_l`|\<mbstring.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [_ismbc (Rutinas)](../../c-runtime-library/ismbc-routines.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb (Rutinas)](../../c-runtime-library/ismbb-routines.md)
