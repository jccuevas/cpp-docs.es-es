---
title: "_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbctolower_l"
  - "_mbctoupper_l"
  - "_mbctoupper"
  - "_mbctolower"
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
  - "mbctoupper_l"
  - "mbctolower_l"
  - "_mbctolower"
  - "_mbctolower_l"
  - "_mbctoupper"
  - "mbctoupper"
  - "mbctolower"
  - "_mbctoupper_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbctolower (función)"
  - "_mbctolower_l (función)"
  - "_mbctoupper (función)"
  - "_mbctoupper_l (función)"
  - "_totlower (función)"
  - "_totupper (función)"
  - "mbctolower (función)"
  - "mbctolower_l (función)"
  - "mbctoupper (función)"
  - "mbctoupper_l (función)"
  - "totlower (función)"
  - "totupper (función)"
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba y convierte las mayúsculas y minúsculas de un carácter multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _mbctolower(  
   unsigned int c   
);  
unsigned int _mbctolower_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctoupper(  
   unsigned int c   
);  
unsigned int _mbctoupper_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter multibyte que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el carácter convertido `c`, si es posible.  De lo contrario, devuelve el carácter `c` sin cambios.  
  
## Comentarios  
 Las funciones prueban un carácter `c` y, si es posible, aplican una de las conversiones siguientes.  
  
|Rutinas|Convierte|  
|-------------|---------------|  
|`_mbctolower,_mbctolower_l`|Carácter en mayúscula en carácter en minúscula.|  
|`_mbctoupper,_mbctoupper_l`|Carácter en minúscula en carácter en mayúscula.|  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión de esta función sin el sufijo `_l` usa la configuración regional actual de este comportamiento dependiente de la configuración regional; la versión con el sufijo `_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbctolower` se denominaba `jtolower` y `_mbctoupper`  se denominaba `jtoupper`.  Para código nuevo, use los nombres nuevos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_t`|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`_mbctolower,_mbctolower_l`|\<mbstring.h\>|  
|`_mbctoupper,_mbctoupper_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_mbbtombc, \_mbbtombc\_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [\_mbcjistojms, \_mbcjistojms\_l, \_mbcjmstojis, \_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctohira, \_mbctohira\_l, \_mbctokata, \_mbctokata\_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [\_mbctombb, \_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)