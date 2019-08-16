---
title: Platform::COMException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: eb6f3e0e4860687d0d47294e11b7741294abac20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500548"
---
# <a name="platformcomexception-class"></a>Platform::COMException (Clase)

Representa los errores COM que se producen durante la ejecución de una aplicación. COMException es la clase base para un conjunto de excepciones estándar predefinidas.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Miembros

La clase COMException hereda de la clase Object y las interfaces IException, IPrintable e IEquatable.

COMException también tiene los siguientes tipos de miembros.

**Constructores**

|Member|DESCRIPCIÓN|
|------------|-----------------|
|[COMException](#ctor)|Inicializa una nueva instancia de la clase COMException.|

**Métodos**

La clase COMException hereda los métodos Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() y ToString() de [Platform::Object Class](../cppcx/platform-object-class.md).

**Propiedades**

La clase COMException tiene las propiedades siguientes.

|Member|DESCRIPCIÓN|
|------------|-----------------|
|[Excepción:: HResult](#hresult)|HRESULT correspondiente a la excepción.|
|[Exception::Message](#message)|Mensaje que describe la excepción.|

## <a name="derived-exceptions"></a>Excepciones derivadas

Las excepciones predefinidas siguientes se derivan de COMException. Difieren de COMException únicamente en su nombre, el nombre de su constructor y el valor HRESULT subyacente.

|NOMBRE|HRESULT subyacente|DESCRIPCIÓN|
|----------|------------------------|-----------------|
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido de una llamada al método COM.|
|AccessDeniedException|E_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|
|ChangedStateException|E_CHANGED_STATE|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Se produce cuando una clase COM no se ha registrado.|
|DisconnectedException|RPC_E_DISCONNECTED|Se produce cuando un objeto se desconecta de sus clientes.|
|FailureException|E_FAIL|Se produce cuando una operación no es correcta.|
|InvalidArgumentException|E_INVALIDARG|Se produce cuando uno de los argumentos proporcionados a un método no es válido.|
|InvalidCastException|E_NOINTERFACE|Se produce cuando un tipo no puede convertirse a otro tipo.|
|NotImplementedException|E_NOTIMPL|Se produce si un método de interfaz no se ha implementado en una clase.|
|NullReferenceException|E_POINTER|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|
|OperationCanceledException|E_ABORT|Se produce cuando se anula una operación.|
|OutOfBoundsException|E_BOUNDS|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|
|OutOfMemoryException|E_OUTOFMEMORY|Se produce cuando la memoria es insuficiente para completar la operación.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a>COMException:: COMException (constructor)

Inicializa una nueva instancia de la clase COMException.

### <a name="syntax"></a>Sintaxis

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parámetros

*hresult*<br/>
Valor HRESULT de error representado por la excepción.

## <a name="hresult"></a>COMException:: HResult (propiedad)

HRESULT correspondiente a la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Valor de propiedad

Valor HRESULT que especifica el error.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre cómo interpretar el valor HRESULT, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes).

## <a name="message"></a>COMException:: Message (propiedad)

Mensaje que describe la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Valor de propiedad

Descripción de la excepción.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
