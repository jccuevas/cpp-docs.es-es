---
title: Clase bad_any_cast
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5172281d1918a8b4ac33bcf412bf4be82b04ef56
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268687"
---
# <a name="badanycast-class"></a>Clase bad_any_cast

Los objetos que se produce un error `any_cast`.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>Funciones miembro

|||
|-|-|
|[what](#what)|Devuelve el tipo.|

## <a name="what"></a> Qué

Devuelve el tipo.

```cpp
const char* what() const noexcept override;
```
