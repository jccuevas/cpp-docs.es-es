---
title: region, endregion
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: c73a90aa2be83d643b74dde4645081e89da3ff73
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037937"
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