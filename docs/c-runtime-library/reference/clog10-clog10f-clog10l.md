---
title: clog10, clog10f, clog10l | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- clog10
- clog10f
- clog10l
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clog10
- clog10f
- clog10l
- complex/clog10
- complex/clog10f
- complex/clog10l
dev_langs: C++
helpviewer_keywords:
- clog10 function
- clog10f function
- clog10l function
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a3e77d3ae6ba74c2a7522492432db6a46db3188
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="clog10-clog10f-clog10l"></a>clog10, clog10f, clog10l
Devuelve el logaritmo en base 10 de un número complejo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_Dcomplex clog10(   
   _Dcomplex z   
);  
_Fcomplex clog10(   
  _Fcomplex z   
);  // C++ only  
_Lcomplex clog10(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clog10f(   
   _Fcomplex z   
);  
_Lcomplex clog10l(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `z`  
 Base del logaritmo.  
  
## <a name="return-value"></a>Valor devuelto  
 Los valores de devolución posibles son:  
  
|parámetro de z|Valor devuelto|  
|-----------------|------------------|  
|Positivo|Logaritmo en base 10 de z|  
|Cero|- ∞|  
|Negativo|NaN|  
|NaN|NaN|  
|+ ∞|+ ∞|  
  
## <a name="remarks"></a>Comentarios  
 Puesto que C++ permite las sobrecargas, es posible llamar a las sobrecargas de `clog10` que toman y devuelven los valores `_Fcomplex` y `_Lcomplex`. En un programa de C, `clog10` siempre toma y devuelve un valor `_Dcomplex` .  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado C|Encabezado C++|  
|-------------|--------------|------------------|  
|`clog10`,               `clog10f`, `clogl`|\<complex.h>|\<ccomplex>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow, cpowf, cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)