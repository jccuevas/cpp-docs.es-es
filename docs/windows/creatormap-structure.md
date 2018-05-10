---
title: CreatorMap (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: a6113737d7463354ffa273ced61b190246f63a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="creatormap-structure"></a>CreatorMap (estructura)
Admite la infraestructura de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>Comentarios  
 Contiene información sobre cómo inicializar, registrar y anular el registro de objetos.  
  
 CreatorMap contiene la información siguiente:  
  
-   Cómo inicializar, registrar y anular el registro de objetos.  
  
-   Cómo se comparan los datos de activación según una fábrica de Windows Runtime o COM clásico.  
  
-   Información sobre el nombre de caché y del servidor de fábrica de una interfaz.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CreatorMap::activationId (miembro de datos)](../windows/creatormap-activationid-data-member.md)|Representa un identificador de objeto que se identifica mediante un identificador de clase COM clásico o un nombre en tiempo de ejecución de Windows.|  
|[CreatorMap::factoryCache (miembro de datos)](../windows/creatormap-factorycache-data-member.md)|Almacena el puntero a la memoria caché del generador para el CreatorMap.|  
|[CreatorMap::factoryCreator (miembro de datos)](../windows/creatormap-factorycreator-data-member.md)|Crea un generador para el CreatorMap especificado.|  
|[CreatorMap::serverName (miembro de datos)](../windows/creatormap-servername-data-member.md)|Almacena el nombre del servidor para el CreatorMap.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CreatorMap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)