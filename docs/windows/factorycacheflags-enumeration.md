---
title: FactoryCacheFlags (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ba3d9b75ff72399e1b9a027c937c24bba4a6c37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags (Enumeración)
Determina si los objetos de generador se almacenan en caché.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, el generador de directiva de caché se especifica como el [ModuleType](../windows/moduletype-enumeration.md) parámetro de plantilla cuando se crea un [módulo](../windows/module-class.md) objeto. Para invalidar esta directiva, especifique un `FactoryCacheFlags` valor cuando se crea un objeto de fábrica.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|Directiva de caché de la `Module` se utiliza el objeto.|  
|`FactoryCacheEnabled`|Habilita el almacenamiento en caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se utiliza para crear un `Module` objeto.|  
|`FactoryCacheDisabled`|Deshabilita el almacenamiento en caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se utiliza para crear un `Module` objeto.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)