---
title: Exception (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs: C++
helpviewer_keywords: Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c2a6ee18779bbd1f54cf33a7b13a60725701c34c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformexception-class"></a>Platform::Exception (Clase)
Representa los errores que se producen durante la ejecución de una aplicación. Las clases de excepción personalizadas no se pueden derivar de `Platform::Exception`. Si necesitas una excepción personalizada, puedes utilizar `Platform::COMException` y especificar un HRESULT específico de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Miembros  
 La clase `Exception` hereda de la clase `Object` y las interfaces `IException`, `IPrintable`y `IEquatable` .  
  
 La clase `Exception` también tiene las siguientes clases de miembros.  
  
### <a name="constructors"></a>Constructores  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[Exception](#ctor)|Inicializa una nueva instancia de la clase `Exception`.|  
  
### <a name="methods"></a>Métodos  
 La clase `Exception` hereda los métodos `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`y `ToString()` de [Platform::Object Class](../cppcx/platform-object-class.md). La clase `Exception` también tiene el método siguiente.  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[Exception:: CreateException](#createexception)|Crea una excepción que representa el valor HRESULT especificado.|  
  
### <a name="properties"></a>Propiedades  
 La clase Exception también tiene las propiedades siguientes.  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[Exception](#hresult)|HRESULT correspondiente a la excepción.|  
|[Exception](#message)|Un mensaje que describe la excepción. Este valor es de solo lectura y se no puede modificarse después de que se haya generado `Exception` .|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  

## <a name="createexception"></a>Exception:: CreateException (método)
Crea una excepción Platform::Exception^ a partir de un valor HRESULT especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parámetros  
 hr  
 Un valor HRESULT que se obtiene normalmente de una llamada a un método COM. Si el valor es 0, que es igual a S_OK, este método inicia [InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) debido a los métodos COM que se realizan correctamente no deben producir excepciones.  
  
 message  
 Cadena que describe el error.  
  
### <a name="return-value"></a>Valor devuelto  
 Una excepción que representa el HRESULT de error.  
  
### <a name="remarks"></a>Comentarios  
 Utiliza este método para crear una excepción a partir de un valor HRESULT devuelto, por ejemplo, desde una llamada a un método de interfaz COM. Puedes utilizar la sobrecarga que toma un parámetro String^ para proporcionar un mensaje personalizado.  
  
 Es muy recomendable utilizar CreateException para crear una excepción fuertemente tipada en lugar de crear un [COMException](../cppcx/platform-comexception-class.md) que simplemente contenga el valor HRESULT.  
  


## <a name="ctor"></a>Constructor Exception
Inicializa una nueva instancia de la clase Exception.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parámetros  
 `hresult`  
 Valor HRESULT de error representado por la excepción.  
  
 `message`  
 Mensaje especificado por el usuario, como texto preceptivo, asociado a la excepción. Normalmente, deberías optar por la segunda sobrecarga para proporcionar un mensaje descriptivo que sea lo más específico posible sobre cómo y por qué se ha producido el error.  
  


## <a name="hresult"></a>Propiedad Exception
HRESULT correspondiente a la excepción.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Valor de propiedad  
 Valor HRESULT.  
  
### <a name="remarks"></a>Comentarios  
 La mayoría de las excepciones comienzan como errores COM, que se devuelven como valores HRESULT. C++/CX convierte estos valores en objetos Platform::Exception^ y esta propiedad almacena el valor del código de error original.  
  


## <a name="message"></a>Propiedad Exception
Mensaje que describe el error.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
public:property String^ Message;  
```  
  
## <a name="property-value"></a>Valor de propiedad  
 En las excepciones que se originan en Windows Runtime, es una descripción del error proporcionada por el sistema.  
  
### <a name="remarks"></a>Comentarios  
 En Windows 8, esta propiedad es de solo lectura porque las excepciones en esa versión de Windows Runtime se transmiten a través de la ABI solo como valores HRESULT. En Windows 8.1, se transmite información de excepción más completa a través de la ABI y puedes proporcionar un mensaje personalizado al que otros componentes podrán tener acceso mediante programación. Para obtener más información, consulte [excepciones (C++ / CX)](../cppcx/exceptions-c-cx.md).  
  

  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)