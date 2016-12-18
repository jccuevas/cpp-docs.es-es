---
title: "Archivos de encabezado requeridos y opcionales | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.headers"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "archivos de encabezado, necesarios en tiempo de ejecución"
  - "archivos de inclusión, necesarios en tiempo de ejecución"
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos de encabezado requeridos y opcionales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Descripción de cada rutinas de servicio incluye una lista de inclusión necesaria y opcional, o el encabezado \(. H\), archivos de esa rutina.  Los archivos de encabezado necesarios deben incluirse para obtener la declaración de función para la rutina o una definición utilizada por otra rutina denominada internamente.  Los archivos de encabezado opcionales se incluyen normalmente para aprovechar de constantes predefinidas, de definiciones de tipo, o de macros especificado.  La tabla siguiente se muestran algunos ejemplos del contenido opcionales del archivo de encabezado:  
  
|Definición|Ejemplo|  
|----------------|-------------|  
|Definición de macro|Si una rutina de biblioteca se implementa como una macro, la definición de macro puede estar en un archivo de encabezado distinto del archivo de encabezado para la rutina original.  Por ejemplo, la macro de `_toupper` se define en el archivo de encabezado CTYPE.H, mientras que la función `toupper` se declara en STDLIB.H.|  
|Constante predefinida|Muchas rutinas de biblioteca hacen referencia a las constantes que se definen en archivos de encabezado.  Por ejemplo, `_open` rutina usa constantes como `_O_CREAT`, que se define en el archivo de encabezado FCNTL.H.|  
|Definiciones de tipo|Algunas rutinas de biblioteca devuelven una estructura o tienen una estructura como argumento.  Por ejemplo, las rutinas de entrada\/salida de la secuencia utilizan una estructura de `FILE`con tipo, que se define en STDIO.H.|  
  
 Los archivos de encabezado de la biblioteca en tiempo de ejecución proporcionan declaraciones de función en el estilo recomendado estándar ANSI\/ISO C.  El compilador realiza la comprobación de tipos en cualquier referencia rutinaria que aparece después de la declaración de función asociada.  Las declaraciones de función son especialmente importantes para las rutinas que devuelven un valor de algún tipo distinto de `int`, que es el valor predeterminado.  Rutinas que no especifique su valor devuelto adecuado en su declaración se considerarán por el compilador devolver `int`, que pueden producir resultados inesperados.  Vea [Comprobación de tipos](../c-runtime-library/type-checking-crt.md) para obtener más información.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)