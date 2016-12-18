---
title: "_set_abort_behavior | Microsoft Docs"
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
  - "_set_abort_behavior"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_abort_behavior"
  - "set_abort_behavior"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_abort_behavior (función)"
  - "anular programas"
  - "set_abort_behavior (función)"
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_abort_behavior
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica la acción que se va a realizar cuando un programa termina de manera anómala.  
  
> [!NOTE]
>  No use la función `abort` para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o depuración.  Las formas de cerrar mediante programación o con la interfaz de usuario una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] no se permiten según los [Requisitos de certificación para una aplicación de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889).  Para obtener más información, vea [Ciclo de vida de la aplicación \(aplicaciones de la Tienda Windows\)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## Sintaxis  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### Parámetros  
 \[in\] `flags`  
 Valor nuevo de marcas `abort`.  
  
 \[in\] `mask`  
 Máscara para establecer bits de marcas `abort`.  
  
## Valor devuelto  
 Valor antiguo de las marcas.  
  
## Comentarios  
 Hay dos marcas `abort`: `_WRITE_ABORT_MSG` y `_CALL_REPORTFAULT`.  `_WRITE_ABORT_MSG` determina si se imprime un mensaje de texto de ayuda cuando un programa termina de manera anómala.  El mensaje indica que la aplicación ha llamado a la función `abort`.  El comportamiento predeterminado es imprimir el mensaje.  `_CALL_REPORTFAULT`, si se establece, especifica que se genere un volcado de bloqueo de Watson está y se notifique cuando se llame a `abort` .  De forma predeterminada, los informes de volcado de bloqueo están habilitado en las compilaciones que no son de depuración.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_abort_behavior`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```c  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
  **Suprimir el mensajes de anulación.  Si lo consigue, este mensaje será la única salida.**    
## Vea también  
 [abort](../../c-runtime-library/reference/abort.md)