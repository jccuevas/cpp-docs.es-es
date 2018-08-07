---
title: FactoryCacheFlags (enumeración) | Microsoft Docs
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
ms.openlocfilehash: cc4bd998368fb325878a81ee4954a2ceec9432fe
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570108"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags (Enumeración)
Determina si los objetos de fábrica se almacenan en caché.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, el generador de directiva de caché se especifica como el [ModuleType](../windows/moduletype-enumeration.md) parámetro de plantilla al crear un [módulo](../windows/module-class.md) objeto. Para reemplazar esta directiva, especifique un **FactoryCacheFlags** valor cuando se crea un objeto de fábrica.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|La directiva de caché de la `Module` se usa el objeto.|  
|`FactoryCacheEnabled`|Permite el almacenamiento en caché de fábrica con independencia de la `ModuleType` parámetro de plantilla que se usa para crear un `Module` objeto.|  
|`FactoryCacheDisabled`|Deshabilita la caché del generador con independencia de la `ModuleType` parámetro de plantilla que se usa para crear un `Module` objeto.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)