---
title: "time_base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.time_base"
  - "std::time_base"
  - "time_base"
  - "locale/std::time_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_base (clase)"
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# time_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase actúa como clase base para las facetas de time\_get de la clase de plantilla, definiendo simplemente el tipo enumerado **dateorder** y varias constantes de este tipo.  
  
## Sintaxis  
  
```  
class time_base : public locale::facet {  
public:  
    enum dateorder {no_order, dmy, mdy, ymd, ydm};  
    time_base(  
        size_t _Refs = 0  
    )  
    ~time_base();  
};  
```  
  
## Comentarios  
 Cada constante caracteriza una forma diferente de ordenar los componentes de una fecha.  Las constantes son:  
  
-   **no\_order** no especifica ningún orden determinado.  
  
-   **dmy** especifica el día order, mes, entonces año, como en el 2 de diciembre de 1979.  
  
-   **mdy** especifica el mes order, día, entonces año, como en el 2 de diciembre de 1979.  
  
-   **ymd** especifica el año de pedidos, mes, entonces día, como en 1979 \/12 \/2.  
  
-   **ydm** especifica el año de pedidos, día, entonces mes, como en 1979: 2 de diciembre  
  
## Requisitos  
 Configuración regional \<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)