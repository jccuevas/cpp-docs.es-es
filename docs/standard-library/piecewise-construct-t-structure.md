---
title: piecewise_contruct_t estructura
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268367"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t estructura

La estructura `piecewise_construct_t` es un tipo de estructura vacía que se usa para mantener independiente constructor y la sobrecarga de funciones. En concreto, `pair` tiene un constructor con `piecewise_construct_t` como el primer argumento, seguido por dos `tuple` argumentos.

## <a name="syntax"></a>Sintaxis

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
