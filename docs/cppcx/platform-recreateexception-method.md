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
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693274"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException (Método)

Este método es para uso interno únicamente y no se ha diseñado para el código del usuario. Use el método Exception:: CreateException en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Parámetros

*recursos humanos*

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Devuelve un nuevo Platform::Exception^, según el HRESULT especificado.
