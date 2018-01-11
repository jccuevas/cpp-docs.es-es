---
title: mbrtoc16, mbrtoc323 | Microsoft Docs
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
- mbrtoc16
- mbrtoc32
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs: C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c24a7426c788ac7ecfc98f3e649397912960505a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32
Convierte el primer carácter multibyte de una cadena estrecha en el carácter UTF-32 o UTF-16 equivalente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t mbrtoc16(   
   char16_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
size_t mbrtoc32(  
   char32_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `destination`  
 Puntero al equivalente de `char16_t` o `char32_t` del carácter multibyte que se va a convertir. Si es null, la función no almacena un valor.  
  
 `source`  
 Puntero a la cadena de caracteres multibyte que se va a convertir.  
  
 `max_bytes`  
 El número máximo de bytes de `source` que se examinarán para un carácter que se va a convertir. Debe ser un valor entre 1 y el número de bytes, incluidos los terminadores null, que permanezcan en `source`.  
  
 `state`  
 Puntero a un objeto de estado de conversión `mbstate_t` usado para interpretar la cadena multibyte en uno o más caracteres de salida.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se ejecuta correctamente, devuelve el valor de la primera de estas condiciones que se aplica, dado el valor `state` actual:  
  
|Valor|Condición|  
|-----------|---------------|  
|0|El siguiente `max_bytes` o menos caracteres convertidos de `source` se corresponden con el carácter ancho nulo, que es el valor almacenado si `destination` no es null.<br /><br /> `state` contiene el estado de desplazamiento inicial.|  
|Entre 1 y `max_bytes`, ambos inclusive|El valor devuelto es el número de bytes de `source` que completan un carácter multibyte válido. El carácter ancho convertido se almacena si `destination` no es null.|  
|-3|El siguiente carácter ancho resultante de una llamada anterior a la función se ha almacenado en `destination` si `destination` no es null. No se consumen bytes de `source` por esta llamada a la función.<br /><br /> Cuando  `source` apunta a un carácter multibyte que requiere más de un carácter ancho para representar (por ejemplo, un par suplente), se actualiza el valor `state` para que la siguiente llamada de función escriba el carácter adicional.|  
|-2|Los siguientes bytes `max_bytes` representan un carácter multibyte incompleto pero potencialmente válido. No se almacena ningún valor en `destination`. Este resultado se puede producir si `max_bytes` es cero.|  
|-1|Se ha producido un error de codificación. Los siguientes `max_bytes` o menos bytes no contribuyen a un carácter multibyte completo y válido. No se almacena ningún valor en `destination`.<br /><br /> `EILSEQ` se almacena en `errno` y no se especifica el estado de la conversión `state` .|  
  
## <a name="remarks"></a>Comentarios  
 La función `mbrtoc16` lee hasta `max_bytes` bytes desde `source` para buscar el primer carácter multibyte válido y completo, y luego almacena el carácter UTF-16 equivalente en `destination`. Los bytes de origen se interpretan según la configuración regional multibyte de subprocesos actual. Si el carácter multibyte requiere más de un carácter de salida UTF-16, como un par suplente, el valor `state` se establece para almacenar el siguiente carácter UTF-16 en `destination` en la siguiente llamada a `mbrtoc16`. La función `mbrtoc32` es idéntica, pero la salida se almacena como carácter UTF-32.  
  
 Si `source` es null, estas funciones devuelven el equivalente de una llamada realizada con argumentos de `NULL` para `destination`, `""` para `source`y `1` para `max_bytes`. Se ignoran los valores pasados de `destination` y `max_bytes` .  
  
 Si `source` no es null, la función empieza al comienzo de la cadena e inspecciona hasta `max_bytes` bytes para determinar el número de bytes necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Si los bytes examinados contienen un carácter multibyte válido y completo, la función convierte el carácter en los caracteres anchos equivalentes de 16 o 32 bits. Si `destination` no es nulo, la función almacena el carácter del primer resultado (y posiblemente único) en el destino. Si se requieren caracteres de salida adicionales, se establece un valor en `state`, de modo que las llamadas posteriores a la función generen los caracteres adicionales y devuelvan el valor -3. Si no se requieren más caracteres de salida, `state` se establece en el estado de desplazamiento inicial.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`mbrtoc16`,                `mbrtoc32`|\<uchar.h>|\<cuchar>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [c16rtomb, c32rtomb](../../c-runtime-library/reference/c16rtomb-c32rtomb1.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbsrtowcs](../../c-runtime-library/reference/mbsrtowcs.md)   
 [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md)