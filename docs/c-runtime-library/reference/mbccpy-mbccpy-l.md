---
title: "_mbccpy, _mbccpy_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbccpy"
  - "_mbccpy_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbccpy"
  - "tccpy"
  - "ftccpy"
  - "mbccpy"
  - "_tccpy"
  - "_ftccpy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbccpy (función)"
  - "_mbccpy_l (función)"
  - "_tccpy (función)"
  - "_tccpy_l (función)"
  - "mbccpy (función)"
  - "mbccpy_l (función)"
  - "tccpy (función)"
  - "tccpy_l (función)"
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _mbccpy, _mbccpy_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copia un carácter multibyte de una cadena en otra.  Hay disponibles versiones más seguras de estas funciones; vea [\_mbccpy\_s, \_mbccpy\_s\_l](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `dest`  
 Destino de la copia.  
  
 `src`  
 Carácter multibyte que se va a copiar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Comentarios  
 La función `_mbccpy` copia un carácter multibyte de `src` en `dest`.  
  
 Esta función valida sus parámetros.  Si se pasa a `_mbccpy` un puntero nulo para `dest` o `src`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL`.  
  
 `_mbccpy` usa la configuración regional actual para cualquier comportamiento que dependa de la configuración regional.  `_mbccpy_l` y `_mbccpy` son exactamente iguales, salvo que `_mbccpy_l` usa la configuración regional que se pasa para todo comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 **Nota de seguridad** Use una cadena terminada en un valor nulo.  El tamaño de la cadena terminada en un valor nulo no debe ser mayor que el del búfer de destino.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tccpy`|Se asigna a una macro o una función insertada|`_mbccpy`|Se asigna a una macro o una función insertada|  
|`_tccpy_l`|no disponible|`_mbccpy_l`|no disponible|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbccpy`|\<mbctype.h\>|  
|`_mbccpy_l`|\<mbctype.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)