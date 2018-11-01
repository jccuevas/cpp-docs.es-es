---
title: Platform (Espacio de nombres) (C++/CX)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform/Platform
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
ms.openlocfilehash: e5d2caa4e784d7d8f7589bca0ef5210c03cb0d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523878"
---
# <a name="platform-namespace-ccx"></a>Platform (Espacio de nombres) (C++/CX)

Contiene tipos integrados que son compatibles con Windows en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
using namespace Platform;
```

### <a name="members"></a>Miembros

**Atributos**

El espacio de nombres Platform contiene atributos, clases, enumeraciones, interfaces y estructuras. La plataforma también contiene espacios de nombres anidados.

|Atributo|Descripción|
|---------------|-----------------|
|Marcas|Indica que una enumeración se puede tratar como un campo de bits, es decir, un conjunto de marcas.|
|MTAThread|Indica que el modelo de subprocesos de una aplicación es un contenedor multiproceso (MTA).|
|STAThread|Indica que el modelo de subprocesamiento de una aplicación es un contenedor uniproceso (STA).|

**Clases**

El espacio de nombres Platform tiene las siguientes clases.

|Clase|Descripción|
|-----------|-----------------|
|[Platform::AccessDeniedException (Clase)](../cppcx/platform-accessdeniedexception-class.md)|Se produce cuando se deniega el acceso a un recurso o a una característica.|
|[Platform::Agile (Clase)](../cppcx/platform-agile-class.md)|Representa como objeto ágil un objeto que no es ágil.|
|[Platform::Array (Clase)](../cppcx/platform-array-class.md)|Representa una matriz unidimensional modificable.|
|[Platform::ArrayReference (Clase)](../cppcx/platform-arrayreference-class.md)|Representa una matriz cuya inicialización está optimizada para minimizar las operaciones de copia.|
|[Platform::Box (Clase)](../cppcx/platform-box-class.md)|Se emplea para declarar un tipo al que se le ha aplicado la conversión boxing que encapsula un tipo de valor como Windows::Foundation::DateTime o int64 cuando ese tipo se pasa a través de la interfaz binaria de aplicación (ABI) o se almacena en una variable de tipo [Platform::Object^](../cppcx/platform-object-class.md).|
|[Platform::ChangedStateException (Clase)](../cppcx/platform-changedstateexception-class.md)|Se produce cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.|
|[Platform::ClassNotRegisteredException (Clase)](../cppcx/platform-classnotregisteredexception-class.md)|Se produce cuando una clase COM no se ha registrado.|
|[Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)|Representa la excepción que se produce cuando se devuelve un valor no reconocido desde una llamada de método COM.|
|[Platform::Delegate (Clase)](../cppcx/platform-delegate-class.md)|Representa la firma de una función de devolución de llamada.|
|[Platform::DisconnectedException (Clase)](../cppcx/platform-disconnectedexception-class.md)|El objeto se ha desconectado de sus clientes.|
|[Platform::Exception (Clase)](../cppcx/platform-exception-class.md)|Representa los errores que se producen durante la ejecución de una aplicación. La clase base de las excepciones.|
|[Platform::FailureException (Clase)](../cppcx/platform-failureexception-class.md)|Se produce cuando hay un error en la operación. Es el equivalente del HRESULT E_FAIL.|
|[Platform::Guid (Clase de valor)](../cppcx/platform-guid-value-class.md)|Representa un GUID en el sistema de tipos de Windows en tiempo de ejecución.|
|[Platform::InvalidArgumentException (Clase)](../cppcx/platform-invalidargumentexception-class.md)|Se produce cuando uno de los argumentos proporcionados a un método no es válido.|
|[Platform::InvalidCastException (Clase)](../cppcx/platform-invalidcastexception-class.md)|Se produce en situaciones de conversión de tipo o conversión explícita de otra naturaleza que no es válida.|
|[Platform::MTAThreadAttribute (Clase)](../cppcx/platform-mtathreadattribute-class.md)|Indica que el modelo de subprocesos de una aplicación es un contenedor multiproceso (MTA).|
|[Platform::NotImplementedException (Clase)](../cppcx/platform-notimplementedexception-class.md)|Se produce si un método de interfaz no se ha implementado en la clase.|
|[Platform::NullReferenceException (Clase)](../cppcx/platform-nullreferenceexception-class.md)|Se produce cuando se intenta desreferenciar una referencia de un objeto null.|
|[Platform::Object (Clase)](../cppcx/platform-object-class.md)|Una clase base que proporciona un comportamiento común.|
|[Platform::ObjectDisposedException (Clase)](../cppcx/platform-objectdisposedexception-class.md)|Se produce cuando se realiza una operación en un objeto desechado.|
|[Platform::OperationCanceledException (Clase)](../cppcx/platform-operationcanceledexception-class.md)|Se produce cuando se anula una operación.|
|[Platform::OutOfBoundsException (Clase)](../cppcx/platform-outofboundsexception-class.md)|Se produce cuando una operación intenta tener acceso a datos que están fuera del intervalo válido.|
|[Platform::OutOfMemoryException (Clase)](../cppcx/platform-outofmemoryexception-class.md)|Se produce cuando la memoria es insuficiente para completar la operación.|
|[Platform::STAThreadAttribute (Clase)](../cppcx/platform-stathreadattribute-class.md)|Indica que el modelo de subprocesamiento de una aplicación es un contenedor uniproceso (STA).|
|[Platform::String (Clase)](../cppcx/platform-string-class.md)|Una colección secuencial de caracteres Unicode que se utiliza para representar texto.|
|[Platform::StringReference (Clase)](../cppcx/platform-stringreference-class.md)|Permite el acceso a los búferes de cadenas con el mínimo de sobrecarga de copia.|
|[Platform::Type (Clase)](../cppcx/platform-type-class.md)|Identifica un tipo integrado mediante una enumeración de categoría.|
|[Platform::ValueType (Clase)](../cppcx/platform-valuetype-class.md)|La clase base para las instancias de tipos de valor.|
|[Platform::WeakReference (Clase)](../cppcx/platform-weakreference-class.md)|Proporciona una referencia débil a los objetos de la clase ref que no incrementa el recuento de referencias.|
|[Platform::WriteOnlyArray (Clase)](../cppcx/platform-writeonlyarray-class.md)|Representa una matriz unidimensional de solo escritura que se utiliza como parámetro de entrada en los métodos que implementan el patrón FillArray.|
|[Platform::WrongThreadException (Clase)](../cppcx/platform-wrongthreadexception-class.md)|Se produce cuando un subproceso llama mediante un puntero de interfaz que es para un objeto proxy que no pertenece al contenedor del subproceso.|

**Implementaciones de interfaces**

El espacio de nombres Platform define las interfaces siguientes.

|Interfaz|Descripción|
|---------------|-----------------|
|[Platform::IBox (Interfaz)](../cppcx/platform-ibox-interface.md)|Se usa para pasar tipos de valor a funciones cuyos parámetros son de tipo Platform::Object^.|
|[Platform::IBoxArray (Interfaz)](../cppcx/platform-iboxarray-interface.md)|Interfaz usada para pasar matrices de tipos de valor a funciones cuyos parámetros son de tipo Platform::Array.|
|[Platform::IDisposable (Interfaz)](../cppcx/platform-idisposable-interface.md)|Se utiliza para liberar recursos no administrados.|

**Enumeraciones**

El espacio de nombres Platform tiene las siguientes enumeraciones.

|Interfaz|Descripción|
|---------------|-----------------|
|[Platform::CallbackContext (Enumeración)](../cppcx/platform-callbackcontext-enumeration.md)|Una enumeración que se utiliza como parámetro del constructor delegado. Determina si se van a calcular las referencias de la devolución de llamada al subproceso de origen o al subproceso llamador.|
|[Platform::TypeCode (Enumeración)](../cppcx/platform-typecode-enumeration.md)|Especifica una categoría numérica que representa un tipo integrado.|

**Estructuras**

El espacio de nombres Platform tiene las siguientes estructuras.

|Estructura|Descripción|
|---------------|-----------------|
|[Platform::Enum (Clase)](../cppcx/platform-enum-class.md)|Representa una constante con nombre.|
|[Platform::Guid (Clase de valor)](../cppcx/platform-guid-value-class.md)|Representa un GUID.|
|[Platform::IntPtr (Clase de valor)](../cppcx/platform-intptr-value-class.md)|Un puntero con signo cuyo tamaño es adecuado para la plataforma (32 bits o 64 bits).|
|[Platform::SizeT (Clase de valor)](../cppcx/platform-sizet-value-class.md)|Un tipo de datos sin signo que se usa para representar el tamaño de un objeto.|
|[Platform::UIntPtr (Clase de valor)](../cppcx/platform-uintptr-value-class.md)|Un puntero sin signo cuyo tamaño es adecuado para la plataforma (32 bits o 64 bits).|

## <a name="see-also"></a>Vea también

[Platform::Collections (Espacio de nombres)](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Runtime::CompilerServices (Espacio de nombres)](../cppcx/platform-runtime-compilerservices-namespace.md)<br/>
[Platform::Runtime::InteropServices (Espacio de nombres)](../cppcx/platform-runtime-interopservices-namespace.md)<br/>
[Platform::Metadata (Espacio de nombres)](../cppcx/platform-metadata-namespace.md)