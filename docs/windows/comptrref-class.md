---
title: ComPtrRef (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aaeb641fc7b2276567edfb30fd36c46db6cfc5ae
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613694"
---
# <a name="comptrref-class"></a>ComPtrRef (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename T
>
class ComPtrRef : public ComPtrRefBase<T>;
```

#### <a name="parameters"></a>Parámetros

*T*  
Un [ComPtr\<T >](../windows/comptr-class.md) tipo o un tipo derivado de éste, no simplemente la interfaz representada por el `ComPtr`.

## <a name="remarks"></a>Comentarios

Representa una referencia a un objeto de tipo `ComPtr<T>`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[ComPtrRef::ComPtrRef (constructor)](../windows/comptrref-comptrref-constructor.md)|Inicializa una nueva instancia de la **ComPtrRef** clase desde el puntero especificado a otro **ComPtrRef** objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ComPtrRef::GetAddressOf (método)](../windows/comptrref-getaddressof-method.md)|Recupera la dirección de un puntero a la interfaz representada por el actual **ComPtrRef** objeto.|
|[ComPtrRef::ReleaseAndGetAddressOf (método)](../windows/comptrref-releaseandgetaddressof-method.md)|Elimina la actual **ComPtrRef** de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la **ComPtrRef** objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[ComPtrRef::operator InterfaceType** (operador)](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Elimina la actual **ComPtrRef** de objetos y devuelve un puntero a una de puntero a la interfaz que se ha representado por la **ComPtrRef** objeto.|
|[ComPtrRef::operator T* (operador)](../windows/comptrref-operator-t-star-operator.md)|Devuelve el valor de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos del objeto ComPtrRef actual.|
|[ComPtrRef::operator void** (operador)](../windows/comptrref-operator-void-star-star-operator.md)|Elimina la actual **ComPtrRef** de objetos, convierte el puntero a la interfaz que se ha representado por la **ComPtrRef** objeto como un puntero-a-puntero-to **void**y, a continuación, Devuelve el puntero de conversión.|
|[ComPtrRef::operator* (operador)](../windows/comptrref-operator-star-operator.md)|Recupera el puntero a la interfaz representada por el actual **ComPtrRef** objeto.|
|[ComPtrRef::operator== (operador)](../windows/comptrref-operator-equality-operator.md)|Indica si dos **ComPtrRef** objetos son iguales.|
|[ComPtrRef::operator!= (operador)](../windows/comptrref-operator-inequality-operator.md)|Indica si dos **ComPtrRef** objetos no son iguales.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)