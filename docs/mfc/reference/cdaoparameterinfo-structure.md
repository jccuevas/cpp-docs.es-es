---
title: CDaoParameterInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b41d26b736ea9f84c53f71dbd71949f74fb8ae52
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo (Estructura)
El `CDaoParameterInfo` estructura contiene información sobre un objeto de parámetro definido para objetos de acceso a datos (DAO).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `m_strName`  
 Nombres de forma exclusiva el objeto de parámetro. Para obtener más información, vea el tema "Nombre de propiedad" en la Ayuda de DAO.  
  
 `m_nType`  
 Un valor que indica el tipo de datos de un objeto de parámetro. Para obtener una lista de los valores posibles, vea el `m_nType` miembro de la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) estructura. Para obtener más información, vea el tema "Tipo de propiedad" en la Ayuda de DAO.  
  
 *m_varValue*  
 El valor del parámetro, almacenado en una [COleVariant](../../mfc/reference/colevariant-class.md) objeto.  
  
## <a name="remarks"></a>Comentarios  
 Las referencias a principal y secundaria anterior indican cómo devuelve la información de la [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) una función miembro de clase `CDaoQueryDef`.  
  
 MFC no encapsula los objetos de parámetro DAO en una clase. Objetos de definición de consulta DAO subyacente MFC `CDaoQueryDef` objetos almacenan parámetros en las colecciones de parámetros. Para obtener acceso a los objetos de parámetro en un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objeto, llame al objeto querydef `GetParameterInfo` un nombre de parámetro en particular o un índice en la colección de parámetros de la función de miembro. Puede usar el [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) función miembro junto con `GetParameterInfo` para recorrer en iteración la colección de parámetros.  
  
 La información recuperada por la [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) función miembro se almacena en un `CDaoParameterInfo` estructura. Llame a `GetParameterInfo` para el objeto de definición de consulta cuyo conjunto de parámetros se almacena el objeto de parámetro.  
  
> [!NOTE]
>  Si desea obtener o establecer sólo el valor de un parámetro, use la [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) y [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) funciones miembro de clase `CDaoRecordset`.  
  
 `CDaoParameterInfo`También define un `Dump` se basa en la función miembro en modo de depuración. Puede usar `Dump` para volcar el contenido de una `CDaoParameterInfo` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef (clase)](../../mfc/reference/cdaoquerydef-class.md)

