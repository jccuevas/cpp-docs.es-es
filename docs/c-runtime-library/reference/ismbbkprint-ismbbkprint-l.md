---
title: _ismbbkprint, _ismbbkprint_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbkprint
- _ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 17b20969e6164dd4457343f3bd9b17598fc7d705
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="ismbbkprint-ismbbkprintl"></a>_ismbbkprint, _ismbbkprint_l
Determina si un carácter multibyte determinado es un signo de puntuación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _ismbbkprint(  
   unsigned int c   
);  
int _ismbbkprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 `_ismbbkprint` devuelve un valor distinto de cero si el entero `c` es un texto no ASCII o un signo de puntuación no ASCII; de lo contrario devuelve 0. Por ejemplo, solo en la página de códigos 932, `_ismbbkprint` comprueba si hay caracteres o signos de puntuación katakana (intervalo: 0xA1 - 0xDF). `_ismbbkprint` usa la configuración regional actual para los valores de caracteres dependientes de la configuración regional. `_ismbbkprint_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ismbbkprint`|\<mbctype.h>|  
|`_ismbbkprint_l`|\<mbctype.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [_ismbb (Rutinas)](../../c-runtime-library/ismbb-routines.md)
