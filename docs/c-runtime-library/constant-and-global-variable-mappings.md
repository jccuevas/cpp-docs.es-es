---
title: "Asignaciones de constantes y de variables globales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_tenviron"
  - "_TEOF"
  - "_tfinddata_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tenviron (función)"
  - "_TEOF (tipo)"
  - "_tfinddata_t (función)"
  - "asignaciones de texto genérico"
  - "tenviron (función)"
  - "TEOF (tipo)"
  - "tfinddatat (función)"
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Asignaciones de constantes y de variables globales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Éstos constante de genérico\- texto, variable global, y las asignaciones de tipo normal se definen en TCHAR.H y dependen de si `_UNICODE` constante o `_MBCS` definida en el programa.  
  
### Asignaciones de constante y la variable global de Genérico\- texto  
  
|Genérico\-texto \- nombre de objeto|SBCS \(\_UNICODE, \_MBCS no definidos\)|\_MBCS definido|\_UNICODE definido|  
|-----------------------------------------|---------------------------------------------|---------------------|------------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## Vea también  
 [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)   
 [Asignaciones de tipos de datos](../c-runtime-library/data-type-mappings.md)   
 [Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)   
 [Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)   
 [Usar asignaciones de texto genérico](../c-runtime-library/using-generic-text-mappings.md)