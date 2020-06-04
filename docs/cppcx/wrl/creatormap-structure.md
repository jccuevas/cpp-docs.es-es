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
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372601"
---
# <a name="creatormap-structure"></a>CreatorMap (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows runtime y no está diseñada para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Observaciones

Contiene información sobre cómo inicializar, registrar y anular el registro de objetos.

`CreatorMap`contiene la siguiente información:

- Cómo inicializar, registrar y anular el registro de objetos.

- Cómo comparar los datos de activación en función de un generador de COM o Windows Runtime clásico.

- Información sobre la caché de fábrica y el nombre del servidor de una interfaz.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Nombre                                          | Descripción
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de Windows en tiempo de ejecución.
[CreatorMap::factoryCache](#factorycache)     | Almacena el puntero a la `CreatorMap`caché de fábrica para el archivo .
[CreatorMap::factoryCreator](#factorycreator) | Crea un generador para `CreatorMap`el archivo .
[CreatorMap::serverName](#servername)         | Almacena el nombre `CreatorMap`del servidor para el archivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CreatorMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="creatormapactivationid"></a><a name="activationid"></a>CreatorMap::activationId

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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
Función que recupera el nombre de tiempo de ejecución de Windows de un objeto.

### <a name="remarks"></a>Observaciones

Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de tiempo de ejecución de Windows.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>CreatorMap::factoryCache

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Observaciones

Almacena el puntero a la `CreatorMap`caché de fábrica para el archivo .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>CreatorMap::factoryCreator

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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

*Entrada*<br/>
Un CreatorMap.

*iidClassFactory*<br/>
El ID de interfaz de un generador de clases.

*fábrica*<br/>
Cuando se completa la operación, la dirección de un generador de clases.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Crea un generador para el CreatorMap especificado.

## <a name="creatormapservername"></a><a name="servername"></a>CreatorMap::serverName

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Observaciones

Almacena el nombre del servidor para CreatorMap.
