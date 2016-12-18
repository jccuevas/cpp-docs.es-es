---
title: "_set_controlfp | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_controlfp"
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
  - "set_controlfp"
  - "_set_controlfp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_controlfp (función)"
  - "funciones de punto flotante, establecer palabra de control"
  - "set_controlfp (función)"
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_controlfp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la palabra de control flotante.  
  
## Sintaxis  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### Parámetros  
 `newControl`  
 Valores de bit de la nueva palabra de control.  
  
 `mask`  
 Máscara de los bits de la nueva palabra de control que se va a definir.  
  
## Valor devuelto  
 Ninguno.  
  
## Comentarios  
 `_set_controlfp` es similar a `_control87`, pero sólo establece la palabra de control flotante a `newControl`.  Los bits de los valores indican el estado de control de punto flotante.  El estado de control flotante permite que el programa cambie la precisión, el redondeo, y los modos de infinito en el paquete de software matemáticos flotante.  También puede máscara o desenmascarar excepciones de punto flotante mediante `_set_controlfp`.  Para obtener más información, vea [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md).  
  
 Se deja de utilizar esta función al compilar con [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) o `/clr:pure` porque Common Language Runtime admite únicamente la precisión flotante predeterminada.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Compatibilidad|  
|------------|--------------------------|--------------------|  
|`_set_controlfp`|\<float.h\>|procesador x86 sólo|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_clear87, \_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)