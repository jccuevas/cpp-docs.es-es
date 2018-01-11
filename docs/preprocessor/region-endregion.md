---
title: "la región, endregion | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs: C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad2eb3d094447ae3ae35b0dbe9dc0fef2fe06710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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