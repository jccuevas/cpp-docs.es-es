---
title: RoInitializeWrapper (clase) | Microsoft Docs
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f5c47ac34d8b159e75acf672ba57ca8c1ebac1e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592834"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)

Inicializa el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
class RoInitializeWrapper
```

## <a name="remarks"></a>Comentarios

**RoInitializeWrapper** es una ventaja que inicializa el tiempo de ejecución de Windows y devuelve un HRESULT que indica si la operación fue correcta. Dado que el destructor de clase llama a `::Windows::Foundation::Uninitialize`, las instancias de **RoInitializeWrapper** debe declararse en el ámbito global o de nivel superior.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[RoInitializeWrapper::RoInitializeWrapper (constructor)](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializa una nueva instancia de la **RoInitializeWrapper** clase.|
|[RoInitializeWrapper::~RoInitializeWrapper (destructor)](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Destruye la instancia actual de la **RoInitializeWrapper** clase.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[RoInitializeWrapper::HRESULT() (operador)](../windows/roinitializewrapper-hresult-parens-operator.md)|Recupera el valor HRESULT producido por la **RoInitializeWrapper** constructor.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RoInitializeWrapper`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)