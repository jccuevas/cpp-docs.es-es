---
title: "FactoryCacheFlags (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::FactoryCacheFlags"
dev_langs: 
  - "C++"
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FactoryCacheFlags (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Determina si los objetos de fábrica se almacenan en caché.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, el generador de directiva de caché se especifica como el [ModuleType](../Topic/ModuleType%20Enumeration.md) parámetro de plantilla al crear un [módulo](../windows/module-class.md) objeto. Para reemplazar esta directiva, especifique un `FactoryCacheFlags` valor cuando se crea un objeto de fábrica.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|Directiva de caché de la `Module` se utiliza el objeto.|  
|`FactoryCacheEnabled`|Habilita la caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se utiliza para crear un `Module` objeto.|  
|`FactoryCacheDisabled`|Deshabilita el almacenamiento en caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se utiliza para crear un `Module` objeto.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres Microsoft:: wrl](../windows/microsoft-wrl-namespace.md)