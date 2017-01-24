---
title: "_cgets_s, _cgetws_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cgetws_s"
  - "_cgets_s"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_cgets_s"
  - "cgets_s"
  - "cgetws_s"
  - "_cgetws_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cgets_s (función)"
  - "_cgetws_s (función)"
  - "cget_s (función)"
  - "cgetws_s (función)"
  - "consola, obtener cadenas de"
  - "cadenas [C++], obtener de consola"
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cgets_s, _cgetws_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene una cadena de caracteres de la consola.  Estas versiones de [\_cgets y \_cgetws](../../c-runtime-library/cgets-cgetws.md) incluyen mejoras de seguridad, tal como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _cgets_s(   
   char *buffer,  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
errno_t _cgetws_s(  
   wchar_t *buffer  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
template <size_t size>  
errno_t _cgets_s(   
   char (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
template <size_t size>  
errno_t _cgetws_s(  
   wchar_t (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 \[in\] `numberOfElements`  
 Tamaño del búfer en caracteres anchos o de un solo byte, que también es el número máximo de caracteres que se va a leer.  
  
 \[in\] `pSizeRead`  
 Número de caracteres que realmente se va a leer.  
  
## Valor devuelto  
 El valor devuelto es cero si es correcto; en caso contrario, un código de error si se produce un error.  
  
### Condiciones de error  
  
|`buffer`|`numberOfElements`|`pSizeRead`|Volver|Contenido de `buffer`|  
|--------------|------------------------|-----------------|------------|---------------------------|  
|`NULL`|cualquiera|cualquiera|`EINVAL`|N\/D|  
|no `NULL`|cero|cualquiera|`EINVAL`|no modificado|  
|no `NULL`|cualquiera|`NULL`|`EINVAL`|cadena de longitud cero|  
  
## Comentarios  
 `_cgets_s` y `_cgetws_s` leen una cadena de la consola y la copian \(con un terminador null\) en `buffer`.  `_cgetws_s` es la versión de caracteres anchos de la función; aparte del tamaño de carácter, el comportamiento de estas dos funciones es idéntico.  El tamaño máximo de la cadena que se va a leer se pasa como parámetro `numberOfElements`.  Este tamaño debe incluir un carácter adicional para el carácter null de terminación.  El número real de caracteres que se leen se coloca en `pSizeRead`.  
  
 Si se produce un error durante la operación o en la validación de los parámetros, se invoca el controlador de parámetro no válido, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve `EINVAL`.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores menos seguras con sus homólogos más seguros y más recientes.  Para obtener más información, consulte [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cgets_s`|\<conio.h\>|  
|`_cgetws_s`|\<conio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_getch, \_getwch](../../c-runtime-library/reference/getch-getwch.md)