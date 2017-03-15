---
title: "2.2 Conditional Compilation | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.2 Conditional Compilation
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El nombre de la macro de**OPENMP** de \_está definido por implementaciones de OpenMP\-conforme a cuando *el yyyymm*constante decimal, que será el año y el mes de la especificación autorizada.  esta macro no debe ser el asunto de **\#define** o de **\#undef** que preprocesa directiva.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Si los proveedores definen extensiones con OpenMP, pueden especificar macros predefinidas adicionales.