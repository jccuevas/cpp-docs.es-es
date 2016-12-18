---
title: "&lt;ccomplex&gt; | Microsoft Docs"
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
  - "<ccomplex>"
dev_langs: 
  - "C++"
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;ccomplex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluye el encabezado de STL [\<complex\>](../standard-library/complex.md) que, en efecto, incluye el encabezado \<complex.h\> de la biblioteca estándar de C y añade los nombres asociados al espacio de nombres `std`.  
  
## Sintaxis  
  
```cpp  
  
#include <ccomplex>  
  
```  
  
## Comentarios  
 Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el espacio de nombres `std`.  
  
 El nombre `clog`, que está declarado en \<complex.h\>, no está definido en el espacio de nombres `std` por los conflictos potenciales con el `clog` que está declarado en [\<iostream\>](../standard-library/iostream.md).  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)