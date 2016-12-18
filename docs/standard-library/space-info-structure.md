---
title: "space_info (Estructura) | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::space_info"
dev_langs: 
  - "C++"
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: 13
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# space_info (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene información sobre un volumen.  
  
## Sintaxis  
  
```  
struct space_info;  
```  
  
## Miembros  
  
### Miembros de datos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`unsigned long long available`|Representa el número de bytes que están disponibles para representar datos en el volumen.|  
|`unsigned long long capacity`|Representa el número total de bytes que el volumen puede representar.|  
|`unsigned long long free`|Representa el número de bytes que no se usan para representar datos en el volumen.|  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::tr2::sys  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [space \(Función\)](http://msdn.microsoft.com/es-es/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md)