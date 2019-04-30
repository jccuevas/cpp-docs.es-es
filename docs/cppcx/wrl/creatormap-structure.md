---
title: CreatorMap (estructura)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398620"
---
# <a name="creatormap-structure"></a>CreatorMap (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Comentarios

Contiene información acerca de cómo inicializar, registrar y anular el registro de objetos.

`CreatorMap`contiene la siguiente información:

- Cómo inicializar, registrar y anular el registro de objetos.

- Cómo se comparan los datos de activación según un generador clásico COM o en tiempo de ejecución de Windows.

- Información sobre el nombre de caché y el servidor de fábrica para una interfaz.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Name                                          | Descripción
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de Windows en tiempo de ejecución.
[CreatorMap::factoryCache](#factorycache)     | Almacena el puntero a la memoria caché del generador para el `CreatorMap`.
[CreatorMap::factoryCreator](#factorycreator) | Crea un generador para el elemento especificado `CreatorMap`.
[CreatorMap::serverName](#servername)         | Almacena el nombre del servidor para el `CreatorMap`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CreatorMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="activationid"></a>CreatorMap::activationId

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
Id. de interfaz.

*getRuntimeName*<br/>
Una función que recupera el nombre de Windows en tiempo de ejecución de un objeto.

### <a name="remarks"></a>Comentarios

Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de Windows en tiempo de ejecución.

## <a name="factorycache"></a>CreatorMap::factoryCache

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Comentarios

Almacena el puntero a la memoria caché del generador para el `CreatorMap`.

## <a name="factorycreator"></a>CreatorMap::factoryCreator

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parámetros

*currentflags*<br/>
Uno de los [RuntimeClassType](runtimeclasstype-enumeration.md) enumeradores.

*entry*<br/>
Un CreatorMap.

*iidClassFactory*<br/>
El identificador de interfaz de un generador de clases.

*factory*<br/>
Cuando se completa la operación, la dirección de un generador de clases.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Crea un generador para el CreatorMap especificado.

## <a name="servername"></a>CreatorMap::serverName

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Comentarios

Almacena el nombre del servidor para el CreatorMap.
