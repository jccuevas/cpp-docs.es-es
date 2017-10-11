---
title: towctrans | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- towctrans
dev_langs:
- C++
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: fcd97b3af0bb7e469db18b1a7ff8290af5df1bc4
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="towctrans"></a>towctrans
Transforma un carácter.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
wint_t towctrans(  
   wint_t c,  
   wctrans_t category   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Carácter que quiere transformar.  
  
 `category`  
 Identificador que contiene el valor devuelto de [wctrans](../../c-runtime-library/reference/wctrans.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Carácter `c`, después de que `towctrans` haya usado la regla de transformación de `category`.  
  
## <a name="remarks"></a>Comentarios  
 El valor de `category` debe haber sido devuelto por una llamada anterior correcta a [wctrans](../../c-runtime-library/reference/wctrans.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`towctrans`|\<wctype.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea `wctrans` para obtener un ejemplo en el que se usa `towctrans`.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)
