---
title: _ismbbblank, _ismbbblank_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbblank_l
- _ismbbblank
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
dev_langs: C++
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 30c47c43c5929eb0c10c584e20e485b9bb724e94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbblank-ismbbblankl"></a>_ismbbblank, _ismbbblank_l
Determina si el carácter multibyte especificado es un carácter en blanco.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _ismbbblank(  
   unsigned int c   
);  
int _ismbbblank_l(  
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
 `_ismbbblank` devuelve un valor distinto de cero si `c` representa un carácter de espacio (0x20), un carácter de tabulación horizontal (0x09) o un carácter específico de la configuración regional que se usa para separar las palabras dentro de una línea de texto para el que `isspace` es «true» (verdadero); en caso contrario, devuelve 0. `_ismbbblank` usa la configuración regional actual para cualquier comportamiento que dependa de la configuración regional. `_ismbbblank_l` es exactamente igual, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ismbbblank`|\<mbctype.h>|  
|`_ismbbblank_l`|\<mbctype.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [_ismbb (Rutinas)](../../c-runtime-library/ismbb-routines.md)