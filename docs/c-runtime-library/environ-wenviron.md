---
title: _environ, _wenviron | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
dev_langs:
- C++
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 277f8a853a5262d524016630f52bfcbfc8a8b18b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="environ-wenviron"></a>_environ, _wenviron
La variable `_environ` es un puntero a una matriz de punteros a las cadenas de caracteres multibyte que constituyen el entorno de proceso. Esta variable global ha quedado en desuso en las versiones funcionales más seguras [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) y [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md), que deben utilizarse en lugar de la variable global. `_environ` está declarado en Stdlib.h.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
extern char **_environ;  
```  
  
## <a name="remarks"></a>Comentarios  
 En un programa que usa la función `main`, `_environ` se inicializa al inicio del programa según la configuración efectuada en el entorno del sistema operativo. El entorno consta de una o varias entradas del formulario  
  
 `ENVVARNAME` `=string`  
  
 `getenv_s` y `putenv_s` usan la variable `_environ` para acceder a la tabla de entorno y modificarla. Al llamar a `_putenv` para agregar o eliminar la configuración del entorno, la tabla de entorno cambia de tamaño. También puede cambiar su ubicación en la memoria, en función de los requisitos de memoria del programa. El valor de `_environ` se ajusta automáticamente según corresponda.  
  
 La variable `_wenviron`, que se declara en Stdlib.h como:  
  
```  
extern wchar_t **_wenviron;  
```  
  
 es una versión con caracteres anchos de `_environ`. En un programa que usa la función `wmain`, `_wenviron` se inicializa al inicio del programa según la configuración efectuada en el entorno del sistema operativo.  
  
 En un programa que usa `main`, `_wenviron` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres multibyte. En la primera llamada a `_wgetenv` o `_wputenv`, se crea un entorno de cadena de caracteres anchos que apunta a `_wenviron`.  
  
 De forma similar, en un programa que usa `wmain`, `_environ` es inicialmente `NULL` porque el entorno está formado por cadenas de caracteres anchos. En la primera llamada a `_getenv` o `_putenv`, se crea un entorno de cadena de caracteres multibyte que apunta a `_environ`.  
  
 Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, cada vez que se llame a `_putenv`, se ejecuta automáticamente una llamada a `_wputenv`, de forma que se correspondan las dos cadenas de entorno.  
  
> [!CAUTION]
>  En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Por lo tanto, podría haber dos cadenas Unicode distintas que se asignan a la misma cadena multibyte.  
  
 Sondear `_environ` en un contexto Unicode no tiene sentido si se usa la vinculación [/MD](../build/reference/md-mt-ld-use-run-time-library.md) o `/MDd`. Para el archivo DLL de CRT, el tipo (ancho o multibyte) del programa es desconocido. Dado que se trata del caso más probable, solo se crea el tipo multibyte.  
  
 En el siguiente pseudocódigo se ilustra cómo puede suceder.  
  
```  
int i, j;  
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:  
                                      // putenv ("env_var_z=string1")  
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:  
                                      // putenv("env_var_z=string2")  
```  
  
 En la notación usada en este ejemplo, las cadenas de caracteres no son literales de cadena de C; en su lugar, son marcadores de posición que representan literales de cadena de entorno de Unicode en la llamada `_wputenv` y las cadenas de entorno multibyte en la llamada `putenv`. Los marcadores de posición de caracteres '`x`' y '`y`' de las dos cadenas de entorno Unicode distintas no se asignan inequívocamente a los caracteres del juego de caracteres multibyte (MBCS) actual. En su lugar, ambas se asignan a algún carácter de MBCS '`z`', que es el resultado predeterminado del intento de convertir las cadenas.  
  
 Por lo tanto, en el entorno multibyte, el valor de "`env_var_z`" después de la primera llamada implícita a `putenv` sería "`string1`", pero este valor se sobrescribiría en la segunda llamada implícita a `putenv`, cuando el valor de "`env_var_z`" se establece en "`string2`". Por lo tanto, el entorno de Unicode (en `_wenviron`) y el entorno multibyte (en `_environ`) serían diferentes según esta serie de llamadas.  
  
## <a name="see-also"></a>Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)