---
title: _ismbbalnum, _ismbbalnum_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbalnum
- _ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
caps.latest.revision: 19
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: baff5ee4871e6cfca7a5a9a1951a0d39f62bc4e7
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="ismbbalnum-ismbbalnuml"></a>_ismbbalnum, _ismbbalnum_l
Determina si un carácter multibyte especificado es alfa o numérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _ismbbalnum(  
   unsigned int c   
);  
int _ismbbalnum_l(  
   unsigned int c   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 `_ismbbalnum` devuelve un valor distinto de cero si la expresión:  
  
```  
isalnum || _ismbbkalnum  
```  
  
 es distinto de cero para `c`o 0 si no lo es.  
  
 La versión de esta función con el sufijo `_l` es idéntica, salvo que usa la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ismbbalnum`|\<mbctype.h>|  
|`_ismbbalnum_l`|\<mbctype.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [_ismbb (Rutinas)](../../c-runtime-library/ismbb-routines.md)
