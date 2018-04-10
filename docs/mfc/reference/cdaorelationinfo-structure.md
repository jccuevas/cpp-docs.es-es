---
title: CDaoRelationInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CDaoRelationInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 047b81ebaa903d2b9bdddcf6c606d1e9fe649482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo (Estructura)
El `CDaoRelationInfo` estructura contiene información sobre una relación definida entre los campos de dos tablas en una [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoRelationInfo  
{  
    CDaoRelationInfo();
*// Constructor  
    CString m_strName;      // Primary  
    CString m_strTable;     // Primary  
    CString m_strForeignTable;              // Primary  
    long m_lAttributes;     // Secondary  
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
    short m_nFields;        // Secondary *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 Nombres de forma exclusiva el objeto de relación. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 *m_strTable*  
 Nombre de la tabla principal en la relación.  
  
 *m_strForeignTable*  
 Nombre de la tabla externa en la relación. Una tabla externa es una tabla que se usa para contener las claves externas. Generalmente, se utiliza una tabla externa para establecer o imponer la integridad referencial. La tabla externa está normalmente en el lado "varios" de una relación uno a varios. Algunos ejemplos de tablas externas son tablas que contienen códigos para las American Estados o provincias canadienses pedidos de clientes.  
  
 `m_lAttributes`  
 Contiene información sobre el tipo de relación. El valor de este miembro puede ser cualquiera de las siguientes acciones:  
  
- **dbRelationUnique** relación es de uno a uno.  
  
- **dbRelationDontEnforce** relación no es aplica (sin integridad referencial).  
  
- **dbRelationInherited** relación existe en una base de datos contiene las dos tablas asociadas.  
  
- **dbRelationLeft** la relación es una combinación izquierda. Una combinación externa izquierda incluye todos los registros de la primera (izquierda) de dos tablas, incluso si no existen valores coincidentes para los registros de la segunda tabla (derecha).  
  
- **dbRelationRight** la relación es una combinación derecha. Una combinación externa derecha incluye todos los registros de la segunda (derecha) de dos tablas, incluso si no existen valores coincidentes para los registros de la primera tabla (izquierda).  
  
- **dbRelationUpdateCascade** actualizaciones se producirán en cascada.  
  
- **dbRelationDeleteCascade** eliminaciones se producirán en cascada.  
  
 `m_pFieldInfos`  
 Un puntero a una matriz de [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) estructuras. La matriz contiene un objeto por cada campo de la relación. El `m_nFields` miembro de datos proporciona un recuento de los elementos de matriz.  
  
 `m_nFields`  
 El número de `CDaoRelationFieldInfo` objetos en el `m_pFieldInfos` miembro de datos.  
  
## <a name="remarks"></a>Comentarios  
 Las referencias a principal y secundaria anterior indican cómo se devuelve la información de la [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función de miembro de clase `CDaoDatabase`.  
  
 Objetos de relación no están representados por una clase de MFC. En su lugar, el objeto DAO subyacente de un objeto MFC de la `CDaoDatabase` clase mantiene una colección de objetos de relación: `CDaoDatabase` proporciona funciones de miembro para tener acceso a algunos elementos individuales de información de la relación, o bien pueden tener acceso a ellos a la vez con un `CDaoRelationInfo` objeto mediante una llamada a la `GetRelationInfo` función de miembro del objeto de base de datos que lo contiene.  
  
 La información recuperada por la [CDaoDatabase::GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) función miembro se almacena en un `CDaoRelationInfo` estructura. `CDaoRelationInfo`También define un `Dump` compila la función miembro en versiones de depuración. Puede usar `Dump` para volcar el contenido de un `CDaoRelationInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [CDaoRelationFieldInfo (estructura)](../../mfc/reference/cdaorelationfieldinfo-structure.md)
