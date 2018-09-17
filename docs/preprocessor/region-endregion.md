---
title: la región, endregion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dac2df26f393b7491d94abdb6d987a8e424723e1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715564"
---
# <a name="region-endregion"></a>region, endregion
`#pragma region` permite especificar un bloque de código que se puede expandir o contraer cuando se usa el [característica de esquematización](/visualstudio/ide/outlining) del Editor de código de Visual Studio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>Parámetros  
*comment*  
(Opcional) Un comentario que se mostrará en el editor de código.  
  
*name*  
(Opcional) El nombre de la región.  Este nombre aparecerá en el editor de código.  
  
## <a name="remarks"></a>Comentarios  
 
`#pragma endregion` marca el final de un `#pragma region` bloque.  
  
Un `#region` bloque debe terminarse con `#pragma endregion`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## <a name="see-also"></a>Vea también  
 
[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)