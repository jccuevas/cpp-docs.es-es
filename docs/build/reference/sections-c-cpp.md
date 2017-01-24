---
title: "SECTIONS (C/C++) | Microsoft Docs"
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
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SECTIONS (instrucción de archivo .def)"
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SECTIONS (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Introduce una sección de una o varias `definitions` que son especificadores de acceso en secciones del archivo de salida del proyecto.  
  
```  
SECTIONS  
definitions  
```  
  
## Comentarios  
 Cada definición debe aparecer en una línea independiente.  La palabra clave `SECTIONS` puede estar en la misma línea que la primera definición o en una línea anterior.  El archivo .def puede contener una o varias instrucciones `SECTIONS`.  
  
 Esta instrucción `SECTIONS` establece atributos para una o varias secciones del archivo imagen, y se puede utilizar para reemplazar los atributos predeterminados para cada tipo de sección.  
  
 El formato para `definitions` es:  
  
 `.section_name specifier`  
  
 donde `.section_name`es el nombre de una sección de la imagen del programa y `specifier`es uno o más de los siguientes modificadores de acceso:  
  
|Modificador|Descripción|  
|-----------------|-----------------|  
|`EXECUTE`|La sección es ejecutable|  
|`READ`|Permite operaciones de lectura en los datos|  
|`SHARED`|Comparte la sección entre todos los procesos que cargan la imagen|  
|`WRITE`|Permite operaciones de escritura en los datos|  
  
 Separe los nombres de especificadores con un espacio.  Por ejemplo:  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS` marca el comienzo de una lista de `definitions` de sección.  Cada `definition` debe aparecer en una línea independiente.  La palabra clave `SECTIONS` puede estar en la misma línea que la primera `definition` o en una línea anterior.  El archivo .def puede contener una o varias instrucciones `SECTIONS`.  La palabra clave `SEGMENTS` se admite como sinónimo de `SECTIONS`.  
  
 Se admiten versiones antiguas de Visual C\+\+:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 La palabra clave `CLASS` se admite por razones de compatibilidad, pero no se tiene en cuenta.  
  
 Un modo equivalente de especificar atributos es con la opción [\/SECTION](../../build/reference/section-specify-section-attributes.md).  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)