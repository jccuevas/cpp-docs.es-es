---
title: srand | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: srand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords: srand
dev_langs: C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 99847da3be2e311ac9cb0da301ed4729705ad9fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="srand"></a>srand
Establece el valor de inicialización inicial para el generador de números pseudoaleatorios.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `seed`  
 Valor de inicialización para la generación de números pseudoaleatorios  
  
## <a name="remarks"></a>Comentarios  
 La función `srand` establece el punto de partida para generar una serie de enteros pseudoaleatorios en el subproceso actual. Para reinicializar el generador y crear la misma secuencia de resultados, llame a la función `srand` y vuelva a usar el mismo argumento de `seed`. Cualquier otro valor de `seed` establece el generador en otro punto de partida en la secuencia pseudoaleatoria. `rand` recupera los números pseudaleatorios que se generan. Si se llama a `rand` antes de hacer ninguna llamada a `srand` se genera la misma secuencia que si se llama a `srand` con `seed` con el valor 1.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`srand`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [rand](../../c-runtime-library/reference/rand.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)