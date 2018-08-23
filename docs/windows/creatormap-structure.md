---
title: CreatorMap (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a622eaa40cedfd7bf22259cf81382290f20f3a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593739"
---
# <a name="creatormap-structure"></a>CreatorMap (estructura)

Admite la infraestructura de la biblioteca de plantillas C++ de Windows en tiempo de ejecución y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Comentarios

Contiene información acerca de cómo inicializar, registrar y anular el registro de objetos.

**CreatorMap** contiene la información siguiente:

- Cómo inicializar, registrar y anular el registro de objetos.

- Cómo se comparan los datos de activación según un generador clásico COM o en tiempo de ejecución de Windows.

- Información sobre el nombre de caché y el servidor de fábrica para una interfaz.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CreatorMap::activationId (miembro de datos)](../windows/creatormap-activationid-data-member.md)|Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre de Windows en tiempo de ejecución.|
|[CreatorMap::factoryCache (miembro de datos)](../windows/creatormap-factorycache-data-member.md)|Almacena el puntero a la memoria caché del generador para el **CreatorMap**.|
|[CreatorMap::factoryCreator (miembro de datos)](../windows/creatormap-factorycreator-data-member.md)|Crea un generador para el elemento especificado **CreatorMap**.|
|[CreatorMap::serverName (miembro de datos)](../windows/creatormap-servername-data-member.md)|Almacena el nombre del servidor para el **CreatorMap**.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CreatorMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)