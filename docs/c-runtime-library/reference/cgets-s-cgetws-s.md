---
title: _cgets_s, _cgetws_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
dev_langs: C++
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28e35d5f2eb2f07cd1b02fa8b1edc3f41b2c2174
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cgetss-cgetwss"></a>_cgets_s, _cgetws_s
Obtiene una cadena de caracteres de la consola. Estas versiones de [_cgets y _cgetws](../../c-runtime-library/cgets-cgetws.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 [out] `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 [in] `numberOfElements`  
 Tamaño del búfer en caracteres anchos o de un solo byte, que también es el número máximo de caracteres que se va a leer.  
  
 [in] `pSizeRead`  
 Número de caracteres que realmente se va a leer.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto es cero si es correcto; en caso contrario, un código de error si se produce un error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`buffer`|`numberOfElements`|`pSizeRead`|Volver|Contenido de `buffer`|  
|--------------|------------------------|-----------------|------------|--------------------------|  
|`NULL`|any|any|`EINVAL`|N/D|  
|no `NULL`|cero|any|`EINVAL`|no modificado|  
|no `NULL`|any|`NULL`|`EINVAL`|cadena de longitud cero|  
  
## <a name="remarks"></a>Comentarios  
 `_cgets_s` y `_cgetws_s` leen una cadena de la consola y la copian (con un terminador null) en `buffer`. `_cgetws_s` es la versión de caracteres anchos de la función; aparte del tamaño de carácter, el comportamiento de estas dos funciones es idéntico. El tamaño máximo de la cadena que se va a leer se pasa como parámetro `numberOfElements`. Este tamaño debe incluir un carácter adicional para el carácter null de terminación. El número real de caracteres que se leen se coloca en `pSizeRead`.  
  
 Si se produce un error durante la operación o en la validación de los parámetros, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve `EINVAL`.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina la necesidad de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores menos seguras con sus homólogos más seguros y más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_cgets_s`|\<conio.h>|  
|`_cgetws_s`|\<conio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [_getch, _getwch](../../c-runtime-library/reference/getch-getwch.md)