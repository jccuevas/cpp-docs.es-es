---
title: WeakReference (Class1) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9b7270a03192a6fcf53f0c2ecfd1af07a216243
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595536"
---
# <a name="weakreference-class1"></a>WeakReference (Class1)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakReference;
```

## <a name="remarks"></a>Comentarios

Representa un *referencia débil* que puede utilizarse con el tiempo de ejecución de Windows o COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

Un **WeakReference** objeto mantiene un *referencia fuerte*, que es un puntero a un objeto y un *recuento de referencia segura*, que es el número de copias de los seguros referencia que se han distribuido por el `Resolve()` método. Aunque el recuento de referencia segura es distinto de cero, la referencia segura no es válida y el objeto es accesible. Cuando el recuento de referencia segura se convierte en cero, la referencia segura no es válida y el objeto no es accesible.

Un **WeakReference** objeto normalmente se utiliza para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, crear un **WeakReference** objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

El **WeakReference** métodos son seguros para subprocesos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[WeakReference::WeakReference (constructor)](../windows/weakreference-weakreference-constructor.md)|Inicializa una nueva instancia de la **WeakReference** clase.|
|[WeakReference::~WeakReference (destructor)](../windows/weakreference-tilde-weakreference-destructor.md)|Desinicializa (destrucción) la instancia actual de la **WeakReference** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[WeakReference::DecrementStrongReference (método)](../windows/weakreference-decrementstrongreference-method.md)|Disminuye el recuento de la referencia segura del actual **WeakReference** objeto.|
|[WeakReference::IncrementStrongReference (método)](../windows/weakreference-incrementstrongreference-method.md)|Incrementa el recuento de referencia segura del actual **WeakReference** objeto.|
|[WeakReference::Resolve (método)](../windows/weakreference-resolve-method.md)|Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia segura es distinto de cero.|
|[WeakReference::SetUnknown (método)](../windows/weakreference-setunknown-method.md)|Establece la referencia segura del actual **WeakReference** objeto en el puntero de interfaz especificado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WeakReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)