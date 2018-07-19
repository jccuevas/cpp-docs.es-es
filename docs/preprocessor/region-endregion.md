---
title: la región, endregion | Documentos de Microsoft
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
ms.openlocfilehash: 5590d2b251d86a9d20b62bfdb3d5bf929e3d92d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839452"
---
# <a name="region-endregion"></a>region, endregion
**#pragma region** permite especificar un bloque de código que se puede expandir o contraer cuando se utiliza el [característica de esquematización](/visualstudio/ide/outlining) del Editor de código de Visual Studio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### <a name="parameters"></a>Parámetros  
 `comment`(opcional)  
 Un comentario que aparecerá en el editor de código.  
  
 *nombre*(opcional)  
 El nombre de la región.  Este nombre aparecerá en el editor de código.  
  
## <a name="remarks"></a>Comentarios  
 **#pragma endregion** marca el final de un **#pragma region** bloque.  
  
 A `#region` bloque debe terminarse con **#pragma endregion**.  
  
## <a name="example"></a>Ejemplo  
  
```  
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