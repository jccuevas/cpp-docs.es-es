---
title: region, endregion (Pragmas)
ms.date: 08/29/2019
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
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222383"
---
# <a name="region-endregion-pragmas"></a>region, endregion (Pragmas)

`#pragma region`permite especificar un bloque de código que se puede expandir o contraer cuando se usa la [característica](/visualstudio/ide/outlining) de esquematización del Editor de Visual Studio Code.

## <a name="syntax"></a>Sintaxis

> **#pragma región** *nombre* de\
> **#pragma endregion** *Comentario* de

### <a name="parameters"></a>Parámetros

*Comentario*\
Opta Comentario que se va a mostrar en el editor de código.

*Name*\
Opta Nombre de la región. Este nombre se muestra en el editor de código.

## <a name="remarks"></a>Comentarios

`#pragma endregion`marca el final de un `#pragma region` bloque.

Un bloque debe terminar en una `#pragma endregion` Directiva. `#region`

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

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
