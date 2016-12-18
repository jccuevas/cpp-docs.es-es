---
title: "offsetof (Macro) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
apitype: "DLLExport"
f1_keywords: 
  - "offsetof"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "offsetof (macro)"
  - "miembros de estructura, desplazamiento"
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# offsetof (Macro)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el desplazamiento de un miembro desde el principio de su estructura primaria.  
  
## Sintaxis  
  
```  
  
        size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### Parámetros  
 *structName*  
 Nombre de la estructura de datos primaria.  
  
 `memberName`  
 Nombre del miembro de la estructura de datos primaria cuyo desplazamiento se determina.  
  
## Valor devuelto  
 `offsetof` devuelve el desplazamiento en bytes del miembro especificado desde el principio de su estructura de datos primaria.  No se define para campos de bits.  
  
## Comentarios  
 La `offsetof` macro devuelve el desplazamiento en bytes de `memberName` desde el principio de la estructura especificada por *structName* como valor de tipo `size_t`.  Puede especificar tipos con la palabra clave `struct`.  
  
> [!NOTE]
>  `offsetof` no es una función y no se puede describir mediante un prototipo de C.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`offsetof`|\<stddef.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)