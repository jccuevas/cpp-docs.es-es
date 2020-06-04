---
title: Platform::COMException (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::COMException::HResult
- VCCORLIB/Platform::COMException::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 1d0d36ec16303d6bdaa5f2344cd5d48fba03c8bf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444295"
---
# <a name="platformcomexception-class"></a>Platform::COMException (Clase)

Representa los errores COM que se producen durante la ejecución de una aplicación. COMException es la clase base para un conjunto de excepciones estándar predefinidas.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Members

La clase COMException hereda de la clase Object y las interfaces IException, IPrintable e IEquatable.

COMException también tiene los siguientes tipos de miembros.

**Constructores**

|Member|Descripción|
|------------|-----------------|
|[COMException](#ctor)|Inicializa una nueva instancia de la clase COMException.|

**Métodos**

La clase COMException hereda los métodos Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() y ToString() de [Platform::Object Class](../cppcx/platform-object-class.md).

**Propiedades**

La clase COMException tiene las propiedades siguientes.

|Member|Descripción|
|------------|-----------------|
|[Excepción:: HResult](#hresult)|HRESULT correspondiente a la excepción.|
|[Exception:: Message](#message)|Mensaje que describe la excepción.|

## <a name="derived-exceptions"></a>Excepciones derivadas

Las excepciones predefinidas siguientes se derivan de COMException. Difieren de COMException únicamente en su nombre, el nombre de su constructor y el valor HRESULT subyacente.

|Nombre|HRESULT subyacente|Descripción|
|----------|------------------------|-----------------|
|COMException|*hresult definido por el usuario*|Se produce cuando se devuelve un HRESULT no reconocido desde una llamada al método COM.|
|AccessDeniedException|E_ACCESSDENIED|Se produce cuando se deniega el acceso a un recurso o a una característica.|
|ChangedStateException|E_CHANGED_STATE|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Se produce cuando no se ha registrado una clase COM.|
|DisconnectedException|RPC_E_DISCONNECTED|Se produce cuando se desconecta un objeto de sus clientes.|
|FailureException|E_FAIL|Se produce cuando ocurre un error en una operación.|
|InvalidArgumentException|E_INVALIDARG|Se produce cuando uno de los argumentos proporcionados a un método no es válido.|
|InvalidCastException|E_NOINTERFACE|Se produce cuando no se puede convertir un tipo a otro tipo.|
|NotImplementedException|E_NOTIMPL|Se produce si no se ha implementado un método de interfaz en una clase.|
|NullReferenceException|E_POINTER|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|
|OperationCanceledException|E_ABORT|Se produce cuando se anula una operación.|
|OutOfBoundsException|E_BOUNDS|Se produce cuando una operación intenta acceder a los datos fuera del intervalo válido.|
|OutOfMemoryException|E_OUTOFMEMORY|Se produce cuando no hay suficiente memoria para completar la operación.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd

## <a name="ctor"></a>COMException:: COMException (constructor)

Inicializa una nueva instancia de la clase COMException.

### <a name="syntax"></a>Sintaxis

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parámetros

*valor*<br/>
Valor HRESULT de error representado por la excepción.

## <a name="hresult"></a>COMException:: HResult (propiedad)

HRESULT correspondiente a la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Valor de la propiedad

Valor HRESULT que especifica el error.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre cómo interpretar el valor HRESULT, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes).

## <a name="message"></a>COMException:: Message (propiedad)

Mensaje que describe la excepción.

### <a name="syntax"></a>Sintaxis

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Valor de la propiedad

Descripción de la excepción.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
