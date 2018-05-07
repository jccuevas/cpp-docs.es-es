---
title: CDaoRelationFieldInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53daaaa5ef4997762342cbfb74ae4d5fa96097d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo (Estructura)
El `CDaoRelationFieldInfo` estructura contiene información sobre un campo en una relación definida para objetos de acceso a datos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 El nombre del campo de la tabla principal de la relación.  
  
 `m_strForeignName`  
 El nombre del campo en la tabla externa de la relación.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de relación de DAO especifica los campos de la tabla principal y los campos de una tabla externa que definen a la relación. Las referencias a principal en la definición de la estructura anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto obtenido mediante una llamada a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)función miembro de clase `CDaoDatabase`.  
  
 Objetos de relación y objetos de campo de relación no están representados por una clase de MFC. En su lugar, DAO objetos objetos MFC subyacentes de la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contienen una colección de objetos de relación, llamado a la colección de relaciones. Cada objeto relation, a su vez, contiene una colección de objetos de campo de la relación. Cada objeto de campo de la relación correlaciona un campo de la tabla principal con un campo en la tabla externa. Tomadas juntas, los objetos de campo de relación definen un grupo de campos de cada tabla, que conjuntamente definen a la relación. `CDaoDatabase` le permite acceder a objetos de relación con un `CDaoRelationInfo` objeto mediante una llamada a la `GetRelationInfo` función miembro. El `CDaoRelationInfo` objeto, a continuación, tiene un miembro de datos, `m_pFieldInfos`, que señala a una matriz de `CDaoRelationFieldInfo` objetos.  
  
 Llame a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro de la que contiene `CDaoDatabase` objeto cuya relaciones es colección almacenan el objeto de relación que le interesen. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto. `CDaoRelationFieldInfo` También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoRelationFieldInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo (estructura)](../../mfc/reference/cdaorelationinfo-structure.md)
