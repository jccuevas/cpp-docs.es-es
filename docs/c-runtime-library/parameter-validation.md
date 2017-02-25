---
title: "Validaci&#243;n de par&#225;metros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parámetros, validación"
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Validaci&#243;n de par&#225;metros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayoría de CRT seguridad\- mejorado funciona y muchas de las funciones preexistentes validan sus parámetros.  Esto podría incluir comprobar los punteros para NULL, comprobar que los enteros por primera vez en un intervalo válido, o el comprobar que los valores de enumeración es válido.  Cuando se encuentra un parámetro no válido, se ejecuta el controlador no válido del parámetro.  
  
## Rutina no válida del controlador de parámetro  
 El comportamiento en tiempo de ejecución de C cuando se encuentra un parámetro no válido es llamar al controlador no válido actualmente asignado del parámetro.  El parámetro no válido predeterminado invoca informes de bloqueo de Watson, que hace que la aplicación que se bloquee y pregunta al usuario si se desea cargar el volcado de memoria a Microsoft para el análisis.  En modo de depuración, un parámetro no válido también da lugar a un error de aserción.  
  
 Este comportamiento se puede cambiar mediante la función [\_set\_invalid\_parameter\_handler, \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) para establecer el controlador no válido de parámetro a la propia función.  Si la función especificada no finaliza la aplicación, el control se devuelve a la función que recibió parámetros no válidos, y estas funciones cesarán la ejecución, devuelven normalmente un código de error, y `errno` establece un código de error.  En muchos casos, el valor de `errno` y el valor devuelto son ambos `EINVAL`, que indica un parámetro no válido.  En algunos casos, un código de error más específico se devuelve, por ejemplo `EBADF` para un puntero de archivo dañado pasado como parámetro.  Para obtener más información sobre errno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Vea también  
 [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)