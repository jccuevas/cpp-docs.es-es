---
title: Recreateexception (método)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330328"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException (Método)

Este método es para uso interno únicamente y no se ha diseñado para el código del usuario. Use el método Exception:: CreateException en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Parámetros

*hr*

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Devuelve un nuevo Platform::Exception^, según el HRESULT especificado.
