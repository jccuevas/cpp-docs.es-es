---
title: "Caracter&#237;sticas de seguridad de CRT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_NONSTDC_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_SECURE_NO_WARNINGS"
  - "desbordamientos del búfer"
  - "búferes [C++], desbordamientos del búfer"
  - "CRT, mejoras de seguridad"
  - "CRT_NONSTDC_NO_DEPRECATE"
  - "CRT_NONSTDC_NO_WARNINGS"
  - "CRT_SECURE_NO_DEPRECATE"
  - "CRT_SECURE_NO_WARNINGS"
  - "advertencias sobre desuso (relacionadas con la seguridad)"
  - "advertencias sobre desuso (relacionadas con la seguridad), deshabilitar"
  - "parámetros [C++], validación"
  - "seguridad [CRT]"
  - "advertencias sobre desuso relacionadas con la seguridad [C++]"
  - "CRT con seguridad mejorada"
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# Caracter&#237;sticas de seguridad de CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchas las funciones CRT tienen más recientes, más seguras versiones.  Si existe una función segura, se marca la más antigua, menos segura versión como desusada y la nueva versión tiene el sufijo de `_s` \(“seguras”\).  
  
 En este contexto, “desusada” sólo significa que el uso de una función no está recomendado; no indica que la función se programa para eliminarse CRT.  
  
 Las funciones seguras no evita o corregir errores de seguridad; en lugar, detecte errores cuando se producen.  Realizan comprobaciones para adicionales condiciones de error y, en el caso de un error, se invoca un controlador de errores \(vea [Validación de parámetros](../c-runtime-library/parameter-validation.md)\).  
  
 Por ejemplo, la función de `strcpy` no tiene ninguna manera de saber si la cadena que está copiando es demasiado grande para el búfer de destino.  Sin embargo, su homólogo seguro, `strcpy_s`, toma el tamaño de búfer como parámetro, lo que puede determinar si una saturación del búfer se produce.  Si utiliza `strcpy_s` para copiar once caracteres en un búfer de diez\- carácter, que es un error en la parte; `strcpy_s` no puede corregir el error, pero puede detectar el error e informar al controlador no válido del parámetro.  
  
## Eliminación de advertencias de desaprobación  
 Hay varias maneras de eliminar las advertencias de la aparición de las más antiguas, menos seguras.  La más simple es simplemente definir `_CRT_SECURE_NO_WARNINGS` o utilizar la directiva pragma de [warning](../preprocessor/warning.md) .  Cualquiera deshabilitará advertencias de desuso, pero por supuesto problemas de seguridad que todavía se produjeron advertencias existen.  Es mucho mejor dejar advertencias de desaprobación habilitadas y aprovechar las nuevas características de seguridad de CRT.  
  
 En C\+\+, la manera más fácil de hacerlo es utilizar [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md), que en muchos casos eliminarán advertencias de desaprobación reemplazando llamadas a funciones obsoletas con llamadas a las nuevas versiones seguras de esas funciones.  Por ejemplo, considere esta llamada desusada a `strcpy`:  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 La definición de `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` como 1 elimina la advertencia cambiando la llamada de `strcpy` a `strcpy_s`, que evita las saturaciones del búfer.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md).  
  
 Para las funciones obsoletas sin sobrecargas de plantilla de seguridad, debe considerar definitivamente actualizar manualmente el código para utilizar las versiones seguras.  
  
 Otro origen de las advertencias de desuso, relacionada con la seguridad, son las funciones de POSIX.  Reemplace los nombres de función de POSIX con sus equivalentes estándar \(por ejemplo, cambie [acceso](../c-runtime-library/reference/access-crt.md) a [\_access](../c-runtime-library/reference/access-waccess.md)\), o deshabilitar las advertencias POSIX\- relacionadas de desuso definiendo `_CRT_NONSTDC_NO_WARNINGS`.  Para obtener más información, vea [Deprecated CRT Functions](http://msdn.microsoft.com/es-es/7e259932-c6c8-4c1a-9637-639e591681a5).  
  
## Características de seguridad adicionales  
 Algunas de las características de seguridad incluyen:  
  
-   `Parameter Validation`.  Los parámetros pasados a funciones CRT se validan, en aseguran funciones y en muchas versiones preexistentes desde funciones.  Esta entre las validaciones:  
  
    -   Comprobar el valores de `NULL` pasados a las funciones.  
  
    -   Comprobar los valores enumerados para la validez.  
  
    -   El comprobar que los valores enteros están en intervalos válidos.  
  
-   Para obtener más información, vea [Validación de parámetros](../c-runtime-library/parameter-validation.md).  
  
-   Un controlador para parámetros no válidos también es accesible para el desarrollador.  Cuando un encontrar un parámetro no válido, en lugar de la aserción y de salir de la aplicación, CRT proporciona una manera de comprobar estos problemas con [\_set\_invalid\_parameter\_handler, \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) funcionan.  
  
-   `Sized Buffers`.  Las funciones seguras requieren que el tamaño de búfer se dedica a cualquier función que escribe en un búfer.  Las versiones seguras validan que el búfer es bastante grande antes de escribir, ayudar a evitar los errores de saturación del búfer peligrosas que pueden permitir que el código malintencionado se ejecute.  Estas funciones devuelven un tipo de `errno` de código de error y se invoca normalmente el controlador no válido de parámetro si el tamaño del búfer es demasiado pequeño.  Funciona que lea de los búferes de entrada, como `gets`, tiene versiones seguras que exigen especificar un tamaño máximo.  
  
-   `Null termination`.  Algunas funciones que permiten cadenas potencialmente no termina tienen versiones seguras que se garantiza que las cadenas son correctamente nulas finalizadas.  
  
-   `Enhanced error reporting`.  Códigos de error de vuelta de las funciones seguras con más información de error disponible con funciones la preexistente.  Las funciones seguras y muchas de las funciones existentes `errno` ahora establecido y devuelven a menudo un código de `errno` tipo también, para proporcionar un mejor informes de errores.  
  
-   `Filesystem security`.  Acceso a archivos seguro admiten de API de E\/S segura del archivo en el caso predeterminado.  
  
-   `Windows security`.  API de proceso seguro aplica directivas de seguridad y permite que las ACL se especifiquen.  
  
-   `Format string syntax checking`.  Las cadenas no válidas se detectan, por ejemplo, con los caracteres de campo incorrectos de tipo en las cadenas de formato de `printf` .  
  
## Vea también  
 [Validación de parámetros](../c-runtime-library/parameter-validation.md)   
 [Sobrecargas de plantilla seguras](../c-runtime-library/secure-template-overloads.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)