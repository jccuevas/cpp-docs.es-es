---
title: "Compiler Options Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "opciones del compilador, macros"
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Compiler Options Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas características específicas del compilador de control de macros.  
  
|||  
|-|-|  
|[\_ATL\_ALL\_WARNINGS](../Topic/_ATL_ALL_WARNINGS.md)|Un símbolo que habilita errores en proyectos convirtió de versiones anteriores de ATL.|  
|[\_ATL\_APARTMENT\_THREADED](../Topic/_ATL_APARTMENT_THREADED.md)|defina si uno o más de los objetos utilizan subproceso controlado.|  
|[\_ATL\_CSTRING\_EXPLICIT\_CONSTRUCTORS](../Topic/_ATL_CSTRING_EXPLICIT_CONSTRUCTORS.md)|Crea a algunos constructores de `CString` explícitos, evitando cualquier conversión no deseada.|  
|[\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)|Defina este macro para utilizar la sintaxis bajo estándar de C\+\+, que produce el error del compilador C4867 cuando una sintaxis no estándar se utiliza para inicializar un puntero a una función miembro.|  
|[\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md)|Defina si uno o más de los objetos libre o el subprocesamiento neutro.|  
|[\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)|Un símbolo que indica el proyecto tendrá objetos marcadas como Both, free o Neutro.  [\_ATL\_FREE\_THREADED](../Topic/_ATL_FREE_THREADED.md) Macro se debe utilizar en su lugar.|  
|[\_ATL\_NO\_AUTOMATIC\_NAMESPACE](../Topic/_ATL_NO_AUTOMATIC_NAMESPACE.md)|Un símbolo que evita el uso predeterminado namespace como ATL.|  
|[\_ATL\_NO\_COM\_SUPPORT](../Topic/_ATL_NO_COM_SUPPORT.md)|Un símbolo que impida que el código COM\-relacionado se compila con el proyecto.|  
|[ATL\_NO\_VTABLE](../Topic/ATL_NO_VTABLE.md)|Un símbolo que evita que el puntero vtable es inicializar en el constructor y el destructor de clase.|  
|[ATL\_NOINLINE](../Topic/ATL_NOINLINE.md)|Un símbolo que indica una función no debe insertadas.|  
|[\_ATL\_SINGLE\_THREADED](../Topic/_ATL_SINGLE_THREADED.md)|Defina si todos los objetos utilizan el modelo de subproceso único.|  
  
## Vea también  
 [Macros](../../atl/reference/atl-macros.md)