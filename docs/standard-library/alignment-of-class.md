---
title: "alignment_of (Clase) | Microsoft Docs"
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
  - "std.tr1.alignment_of"
  - "std::tr1::alignment_of"
  - "alignment_of"
  - "std.alignment_of"
  - "std::alignment_of"
  - "type_traits/std::alignment_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "alignment_of (clase) [TR1]"
  - "alignment_of"
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alignment_of (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una alineación del tipo especificado.  Este struct se implementa en términos de [alignof](../cpp/alignof-and-alignas-cpp.md).  Use `alignof` directamente cuando solo sea necesario consultar un valor de alineación.  Use alignment\_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct alignment_of;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 La consulta de tipo contiene el valor de la alineación del tipo `Ty`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [aligned\_storage \(Clase\)](../standard-library/aligned-storage-class.md)