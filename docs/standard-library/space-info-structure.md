---
title: space_info (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd245eb92c571be08e43b6c9e0008ed8e8b94f4b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="spaceinfo-structure"></a>space_info (Estructura)
Contiene información sobre un volumen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`unsigned long long available`|Representa el número de bytes que están disponibles para representar datos en el volumen.|  
|`unsigned long long capacity`|Representa el número total de bytes que el volumen puede representar.|  
|`unsigned long long free`|Representa el número de bytes que no se usan para representar datos en el volumen.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<filesystem >  
  
 **Espacio de nombres:** std::experimental::filesystem  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [space](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)

