---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 6d9429aa7c079f0f99a936019e5945092dc1f006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181530"
---
# <a name="allocate"></a>allocate

**Específicos de Microsoft**

El especificador de declaración de **asignación** nombra un segmento de datos en el que se asignará el elemento de datos.

## <a name="syntax"></a>Sintaxis

```
   __declspec(allocate("segname")) declarator
```

## <a name="remarks"></a>Observaciones

El nombre *segname* se debe declarar mediante una de las siguientes pragmas:

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [section](../preprocessor/section.md)

## <a name="example"></a>Ejemplo

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
