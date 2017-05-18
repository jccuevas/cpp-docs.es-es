---
title: CDaoRelationFieldInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 23d7497502f611cf2311e574556186dc5f7c7d3d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
 Un objeto de relación DAO especifica los campos de una tabla principal y los campos de una tabla externa que definen a la relación. Las referencias al principal en la definición de la estructura anterior indican cómo se devuelve la información en el `m_pFieldInfos` miembro de un [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto obtenido mediante una llamada a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro de clase `CDaoDatabase`.  
  
 Objetos de relación y objetos de campo de la relación no se representan mediante una clase MFC. En su lugar, los objetos DAO subyacentes objetos MFC de la clase [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) contienen una colección de objetos de relación, denominada colección de relaciones. Cada objeto relation, a su vez, contiene una colección de objetos de campo de la relación. Cada objeto de campo de la relación correlaciona un campo de la tabla principal con un campo en la tabla externa. Conjuntamente, los objetos de campo de relación definen un grupo de campos de cada tabla, que conjuntamente definen a la relación. `CDaoDatabase`le permite acceder a los objetos de relación con un `CDaoRelationInfo` objeto mediante una llamada a la `GetRelationInfo` función miembro. El `CDaoRelationInfo` objeto, a continuación, tiene un miembro de datos `m_pFieldInfos`, que apunta a una matriz de `CDaoRelationFieldInfo` objetos.  
  
 Llame a la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro de la que contiene `CDaoDatabase` cuyo almacenan el objeto de relación que le interesa es la colección de relaciones de objeto. A continuación, obtener acceso a la `m_pFieldInfos` miembro de la [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) objeto. `CDaoRelationFieldInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoRelationFieldInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo (estructura)](../../mfc/reference/cdaorelationinfo-structure.md)

