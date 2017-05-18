---
title: _putenv, _wputenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs:
- C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: 22
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: d91f7b780c8f17fbe1e12a195b6a7cf2eaad3d2f
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="putenv-wputenv"></a>_putenv, _wputenv
Crea, modifica o quita variables de entorno. Hay disponibles versiones más seguras de estas funciones; vea [_putenv_s, _wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `envstring`  
 Definición de cadena de entorno.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si es correcto o -1 si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_putenv` agrega nuevas variables de entorno o modifica los valores de las existentes. Las variables de entorno definen el entorno en el que se ejecuta un proceso (por ejemplo, la ruta de búsqueda predeterminada para vincular bibliotecas a un programa). `_wputenv` es una versión con caracteres anchos de `_putenv`; el argumento `envstring` para `_wputenv` es una cadena de caracteres anchos.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 El argumento `envstring` debe ser un puntero a una cadena con el formato `varname=string`, donde `varname` es el nombre de la variable de entorno que se va a agregar o modificar y `string` es el valor de la variable. Si `varname` ya forma parte del entorno, su valor se sustituye por `string`; si no es así, la nueva variable de `varname` y su valor de `string` se agregan al entorno. Una variable se puede quitar del entorno especificando un parámetro `string` vacío, es decir, especificando únicamente `varname=`.  
  
 `_putenv` y `_wputenv` solo afectan al entorno que es local en el proceso actual. No se pueden usar para modificar el entorno del nivel de comandos. Dicho de otro modo, estas funciones solo funcionan en estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el segmento de entorno creado para un proceso por el sistema operativo. Cuando finaliza el proceso actual, el entorno vuelve al nivel del proceso de llamada (en la mayoría de los casos, el nivel del sistema operativo). Sin embargo, el entorno modificado se puede pasar a cualquier proceso nuevo creado por `_spawn`, `_exec` o `system`. Estos nuevos procesos obtienen los elementos nuevos agregados por `_putenv` y `_wputenv`.  
  
 No cambie una entrada de entorno directamente: en lugar de ello, use `_putenv` o `_wputenv` para cambiarla. Especialmente, la liberación directa de elementos de la matriz global `_environ[]` podría dar lugar a que se obtenga acceso a memoria no válida.  
  
 `getenv` y `_putenv` usan la variable global `_environ` para obtener acceso a la tabla de entorno. `_wgetenv` y `_wputenv` usan `_wenviron`. `_putenv`y `_wputenv` podrían cambiar el valor de `_environ` y `_wenviron`, e invalidar así el `_envp` argumento pasado a `main` y `_wenvp` argumento pasado a `wmain`. Por ello, es más seguro usar `_environ` o `_wenviron` para obtener acceso a la información del entorno. Para obtener más información sobre la relación de `_putenv` y `_wputenv` con las variables globales, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  Los grupos de funciones de `_putenv` y `_getenv` no son seguros para subprocesos. `_getenv` podría devolver un puntero de cadena mientras `_putenv` modifica la cadena, y se generarían errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_putenv`|\<stdlib.h>|  
|`_wputenv`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_putenv`, vea [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)
