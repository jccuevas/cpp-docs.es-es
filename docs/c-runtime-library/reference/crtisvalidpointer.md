---
title: _CrtIsValidPointer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtIsValidPointer
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
apitype: DLLExport
f1_keywords:
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: 13
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
ms.openlocfilehash: 021277c17252d18ee0127d710b3a64b3d25fd6d9
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer
Comprueba que un puntero no es null. En las versiones de la biblioteca en tiempo de ejecución de C anteriores a Visual Studio 2010, comprueba que un intervalo de memoria especificado es válido para lectura y escritura (solo en la versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 dirección  
 Señala al comienzo del intervalo de memoria cuya validez se va a comprobar.  
  
 `size`  
 Tamaño del intervalo de memoria especificado, en bytes.  
  
 access  
 Accesibilidad de lectura y escritura que se va a determinar para el intervalo de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 `_CrtIsValidPointer` devuelve TRUE si el puntero especificado no es null. En las versiones de la biblioteca de CRT anteriores a Visual Studio 2010, devuelve TRUE si el intervalo de memoria es válido para la o las operaciones especificadas. De lo contrario, la función devuelve el FALSE.  
  
## <a name="remarks"></a>Comentarios  
 A partir de la biblioteca de CRT de Visual Studio 2010, se ignoran los parámetros de acceso y tamaño, y `_CrtIsValidPointer` solo comprueba que la dirección especificada no es null. No se recomienda usar esta función porque puede realizar la prueba sin ningún problema. En las versiones anteriores a Visual Studio 2010, la función comprueba que el intervalo de memoria que empieza en `address` y se extiende por `size` bytes es válido para la o las operaciones de accesibilidad especificadas. Si `access` se establece en TRUE, el intervalo de memoria se comprueba para operaciones de lectura y escritura. Si `access` es FALSE, el intervalo de memoria solo se comprueba para operaciones de lectura. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtIsValidPointer` se quitan durante el preprocesamiento.  
  
 Dado que esta función devuelve TRUE o FALSE, se puede pasar a una de las macros [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si el intervalo de memoria no es válido para operaciones de lectura y escritura:  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 Para obtener más información sobre cómo usar `_CrtIsValidPointer` con otras macros y funciones de depuración, consulte [Macros para los informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtIsValidPointer`|\<crtdbg.h>|  
  
 `_CrtIsValidPointer` es una extensión de Microsoft. Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo del tema [_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
