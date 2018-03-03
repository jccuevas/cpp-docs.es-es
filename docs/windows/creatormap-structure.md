---
title: CreatorMap (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a941f052527b3617772bcb18b2092fdc35ea3a22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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