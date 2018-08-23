---
title: WeakRef (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96aa076bb8285154f3b340e9e39ae36ed621522f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612738"
---
# <a name="weakref-class"></a>WeakRef (Clase)

Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.

## <a name="syntax"></a>Sintaxis

```cpp
class WeakRef : public ComPtr<IWeakReference>
```

## <a name="remarks"></a>Comentarios

Un **WeakRef** objeto mantiene un *referencia fuerte*, que está asociado a un objeto y puede ser válido o no es válido. Llame a la `As()` o `AsIID()` método para obtener una referencia segura. Cuando la referencia segura se válida, puede obtener acceso al objeto asociado. Cuando la referencia segura no es válida (**nullptr**), el objeto asociado es inaccesible.

Un **WeakRef** objeto normalmente se utiliza para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, crear un **WeakRef** objeto a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.

Tenga en cuenta que hay un cambio de comportamiento en los métodos [As](../windows/weakref-as-method.md), [AsIID](../windows/weakref-asiid-method.md) y [CopyTo](../windows/weakref-copyto-method.md) en el SDK de Windows 10. Anteriormente, después de llamar a cualquiera de estos métodos, consulte la WeakRef para **nullptr** para determinar si se obtuvo correctamente una referencia segura, como se muestra en el código siguiente:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)  
{
    wprintf(L"Couldn’t get strong ref!");
}
```

El código anterior no funciona al usar el SDK de Windows 10 (o posterior). En su lugar, compruebe el puntero que se pasó para **nullptr**.

```cpp
if (strongRef == nullptr)  
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::WeakRef (constructor)](../windows/weakref-weakref-constructor.md)|Inicializa una nueva instancia de la **WeakRef** clase.|
|[WeakRef::~WeakRef (destructor)](../windows/weakref-tilde-weakref-destructor.md)|Desinicializa la instancia actual de la **WeakRef** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::As (método)](../windows/weakref-as-method.md)|Establece el texto especificado `ComPtr` parámetro de puntero para representar la interfaz especificada.|
|[WeakRef::AsIID (método)](../windows/weakref-asiid-method.md)|Establece el texto especificado `ComPtr` parámetro de puntero para representar el identificador de interfaz especificado.|
|[WeakRef::CopyTo (método)](../windows/weakref-copyto-method.md)|Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[WeakRef::operator& (operador)](../windows/weakref-operator-ampersand-operator.md)|Devuelve un `ComPtrRef` objeto que representa el actual **WeakRef** objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)