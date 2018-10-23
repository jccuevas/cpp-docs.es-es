---
title: la región, endregion | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: 2e360009eb9126604d4466daed2445c7dfc582d4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808074"
---
# <a name="region-endregion"></a>region, endregion

`#pragma region` permite especificar un bloque de código que se puede expandir o contraer cuando se usa el [característica de esquematización](/visualstudio/ide/outlining) del Editor de código de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>Parámetros

*comment*<br/>
(Opcional) Un comentario que se mostrará en el editor de código.

*name*<br/>
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